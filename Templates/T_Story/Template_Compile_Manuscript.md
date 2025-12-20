<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let manuscriptFileName;
let manuscriptTitle;
let selectedStory;

if (hasNewStoryTitle || hasUntitledTitle) {
    // Get all existing Story notes
    const storyFiles = app.vault.getFiles()
        .filter(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title;
        });
    
    if (storyFiles.length > 0) {
        // Create arrays for suggester
        const storyTitles = storyFiles.map(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache.frontmatter.story_title;
        });
        
        // Let user select from existing stories
        selectedStory = await tp.system.suggester(storyTitles, storyTitles);
        
        if (!selectedStory) {
            // User cancelled selection
            return;
        }
    } else {
        // No existing stories found
        new Notice("No existing stories found. Create a Story note first.");
        return;
    }
    
    // Prompt for manuscript title (for the title property, not filename)
    manuscriptTitle = await tp.system.prompt("Manuscript title:", selectedStory);
    if (!manuscriptTitle) return; // User cancelled
    
    // Set filename with -Manuscript suffix
    manuscriptFileName = `${selectedStory}-Manuscript`;
    
    await tp.file.rename(manuscriptFileName);
} else {
    manuscriptFileName = tp.file.title;
    // Extract story name from current file if possible
    selectedStory = manuscriptFileName.replace("-Manuscript", "");
    manuscriptTitle = selectedStory;
}

// Prompt for manuscript metadata
const author = await tp.system.prompt("Author name:", "Your Name");
const subtitle = await tp.system.prompt("Subtitle (optional):", "");
const date = await tp.system.prompt("Date:", tp.date.now("YYYY-MM-DD"));

// Get all scene files for this story
const sceneFiles = app.vault.getFiles()
    .filter(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache?.frontmatter?.story_title === selectedStory &&
               file.path.includes("/Scenes/");
    });

if (sceneFiles.length === 0) {
    new Notice(`No scenes found for story: ${selectedStory}`);
}

// Sort by story_order
sceneFiles.sort((a, b) => {
    const cacheA = app.metadataCache.getFileCache(a);
    const cacheB = app.metadataCache.getFileCache(b);
    const orderA = cacheA?.frontmatter?.story_order || "999";
    const orderB = cacheB?.frontmatter?.story_order || "999";
    
    // Handle chapter.scene.beat format (1.2.3)
    const partsA = orderA.toString().split('.').map(Number);
    const partsB = orderB.toString().split('.').map(Number);
    
    for (let i = 0; i < Math.max(partsA.length, partsB.length); i++) {
        const a = partsA[i] || 0;
        const b = partsB[i] || 0;
        if (a !== b) return a - b;
    }
    return 0;
});

// Move file to Story folder first
const targetFolder = `Story/${selectedStory}`;
await tp.file.move(`${targetFolder}/${manuscriptFileName}`);

// Group scenes by chapter and build embeds with chapter headings
let currentChapter = null;
let embedSections = [];

for (const file of sceneFiles) {
    const cache = app.metadataCache.getFileCache(file);
    const order = cache?.frontmatter?.story_order || "999";
    const chapterNum = order.toString().split('.')[0];
    
    // Add chapter heading when we encounter a new chapter
    if (chapterNum !== currentChapter) {
        currentChapter = chapterNum;
        embedSections.push(`\n# Chapter ${chapterNum}\n`);
    }
    
    // Add the scene embed
    const noteName = file.basename;
    embedSections.push(`![[${noteName}]]`);
}

const embeds = embedSections.join('\n\n');

new Notice(`Manuscript compiled: ${sceneFiles.length} scenes in ${currentChapter || 0} chapters`);
_%>---
title: <% manuscriptTitle %>
author: <% author %><% subtitle ? `\nsubtitle: ${subtitle}` : '' %>
date: <% date %>
---
<!-- `CTRL+P`, search “Pandoc” and export to your format of choice. -->
<% embeds %>