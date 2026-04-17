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
    new Notice("Compile Manuscript: Creates a markdown file linking all chapters from a draft, ordered by chapter number. Exported file is saved to the story's root folder.", 8000);

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

    // Delete any existing manuscript before renaming to avoid conflicts
    const existingManuscript = app.vault.getFiles().find(f =>
        f.basename === manuscriptFileName &&
        f.path.startsWith(`Story/${selectedStory}/`) &&
        f !== tp.config.target_file
    );
    if (existingManuscript) {
        await app.vault.delete(existingManuscript);
    }

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

// Select export format
const exportFormats = [
    { label: "Word Document (docx)", id: "docx" },
    { label: "OpenDocument (odt)", id: "odt" },
    { label: "ePub", id: "epub" },
    { label: "HTML", id: "html" },
    { label: "Skip export", id: null },
];
const formatLabels = exportFormats.map(f => f.label);
const formatIds = exportFormats.map(f => f.id);
const selectedFormat = await tp.system.suggester(formatLabels, formatIds, false, "Export format?");
// null from "Skip export" or undefined from cancellation — both just skip

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

// Move file to Story folder
const targetFolder = `Story/${selectedStory}`;
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

// Auto-execute Pandoc export after Templater finishes rendering
if (selectedFormat) {
    setTimeout(() => {
        app.commands.executeCommandById(`obsidian-pandoc:pandoc-export-${selectedFormat}`);
    }, 1000);
}
_%>---
title: <% manuscriptTitle %>
author: <% author %><% subtitle ? `\nsubtitle: ${subtitle}` : '' %>
date: <% date %>
---
<% embeds %>
