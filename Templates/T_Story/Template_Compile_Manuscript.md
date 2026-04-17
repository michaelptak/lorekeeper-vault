<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let manuscriptFileName;
let manuscriptTitle;
let selectedStory;
let selectedDraft;

const abort = async (msg) => {
    new Notice(msg, 5000);
    const f = tp.config.target_file;
    setTimeout(() => app.vault.delete(f), 500);
};

if (hasNewStoryTitle || hasUntitledTitle) {
    // Get all existing Story notes
    const storyFiles = app.vault.getFiles()
        .filter(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title;
        });

    if (storyFiles.length > 0) {
        const storyTitles = [...new Set(storyFiles.map(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache.frontmatter.story_title;
        }))];

        selectedStory = await tp.system.suggester(storyTitles, storyTitles);
        if (!selectedStory) { await abort("Manuscript compilation cancelled."); return; }
    } else {
        await abort("No existing stories found. Create a Story note first.");
        return;
    }

    // Find the active dashboard for this story
    const matchingStoryFiles = storyFiles.filter(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache.frontmatter.story_title === selectedStory;
    });
    const activeStoryFile = matchingStoryFiles.find(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache.frontmatter.active_draft === true;
    }) || matchingStoryFiles[0];
    const activeCache = app.metadataCache.getFileCache(activeStoryFile);
    const activeDraft = activeCache?.frontmatter?.draft || 1;

    // Discover available drafts
    const storyPath = `Story/${selectedStory}`;
    const allFolders = app.vault.getAllFolders();
    const draftNumbers = allFolders
        .filter(f => f.path.startsWith(storyPath + "/Draft "))
        .map(f => {
            const match = f.path.match(/Draft (\d+)$/);
            return match ? parseInt(match[1]) : null;
        })
        .filter(n => n !== null)
        .sort((a, b) => b - a);

    if (draftNumbers.length === 0) {
        await abort("No drafts found. Create a chapter first.");
        return;
    }

    // Select draft (skip prompt if only one)
    if (draftNumbers.length === 1) {
        selectedDraft = draftNumbers[0];
    } else {
        const draftLabels = draftNumbers.map(n => `Draft ${n}${n === activeDraft ? " (active)" : ""}`);
        selectedDraft = await tp.system.suggester(draftLabels, draftNumbers, false, "Compile which draft?");
        if (selectedDraft === null || selectedDraft === undefined) { await abort("Manuscript compilation cancelled."); return; }
    }

    // Prompt for manuscript metadata
    manuscriptTitle = await tp.system.prompt("Manuscript title:", selectedStory);
    if (!manuscriptTitle) { await abort("Manuscript compilation cancelled."); return; }

    manuscriptFileName = `${selectedStory}-Draft ${selectedDraft}-Manuscript`;
    await tp.file.rename(manuscriptFileName);
} else {
    manuscriptFileName = tp.file.title;
    const match = manuscriptFileName.match(/^(.+)-Draft (\d+)-Manuscript$/);
    if (match) {
        selectedStory = match[1];
        selectedDraft = parseInt(match[2]);
    } else {
        selectedStory = manuscriptFileName.replace("-Manuscript", "");
        selectedDraft = 1;
    }
    manuscriptTitle = selectedStory;
}

// Prompt for remaining metadata
const author = await tp.system.prompt("Author name:", "Your Name");
const subtitle = await tp.system.prompt("Subtitle (optional):", "");
const date = await tp.system.prompt("Date:", tp.date.now("YYYY-MM-DD"));

// Get all chapter files for this story + draft
const draftPath = `Story/${selectedStory}/Draft ${selectedDraft}`;
const chapterFiles = app.vault.getFiles()
    .filter(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache?.frontmatter?.story_title === selectedStory &&
               file.path.startsWith(draftPath + "/");
    });

if (chapterFiles.length === 0) {
    new Notice(`No chapters found in ${draftPath}`);
}

// Sort by chapter-number (dot-notation: 1.2.3)
chapterFiles.sort((a, b) => {
    const cacheA = app.metadataCache.getFileCache(a);
    const cacheB = app.metadataCache.getFileCache(b);
    const orderA = cacheA?.frontmatter?.["chapter-number"] || "999";
    const orderB = cacheB?.frontmatter?.["chapter-number"] || "999";

    const partsA = orderA.toString().split('.').map(Number);
    const partsB = orderB.toString().split('.').map(Number);

    for (let i = 0; i < Math.max(partsA.length, partsB.length); i++) {
        const a = partsA[i] || 0;
        const b = partsB[i] || 0;
        if (a !== b) return a - b;
    }
    return 0;
});

// Move file to Story folder, overwriting any existing manuscript
const targetFolder = `Story/${selectedStory}`;
const existingManuscript = app.vault.getFileByPath(`${targetFolder}/${manuscriptFileName}.md`);
if (existingManuscript) {
    await app.vault.delete(existingManuscript);
}
await tp.file.move(`${targetFolder}/${manuscriptFileName}`);

// Group chapters by integer part and build embeds with chapter headings
let currentChapter = null;
let embedSections = [];

for (const file of chapterFiles) {
    const cache = app.metadataCache.getFileCache(file);
    const order = cache?.frontmatter?.["chapter-number"] || "999";
    const chapterNum = order.toString().split('.')[0];

    if (chapterNum !== currentChapter) {
        currentChapter = chapterNum;
        embedSections.push(`\n# Chapter ${chapterNum}\n`);
    }

    const noteName = file.basename;
    embedSections.push(`![[${noteName}]]`);
}

const embeds = embedSections.join('\n\n');

new Notice(`Manuscript compiled: ${chapterFiles.length} chapters from Draft ${selectedDraft}`);
_%>---
title: <% manuscriptTitle %>
author: <% author %><% subtitle ? `\nsubtitle: ${subtitle}` : '' %>
date: <% date %>
---
<!-- `CTRL+P`, search "Pandoc" and export to your format of choice. -->
<% embeds %>
