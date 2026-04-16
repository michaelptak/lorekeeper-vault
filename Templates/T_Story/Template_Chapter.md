<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
let selectedStory;
let selectedDraft;

// Helper: abort and clean up the temporary file
const abort = async (msg) => {
    new Notice(msg, 5000);
    const f = tp.config.target_file;
    setTimeout(() => app.vault.delete(f), 500);
    return;
};

if (hasNewStoryTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Chapter Name");
    if (!title) { await abort("Chapter creation cancelled."); return; }

    // Try to infer story from a visible Story-tagged note in the workspace
    const leaves = app.workspace.getLeavesOfType("markdown");
    for (const leaf of leaves) {
        const file = leaf.view?.file;
        if (file) {
            const cache = app.metadataCache.getFileCache(file);
            if (cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title) {
                selectedStory = cache.frontmatter.story_title;
                selectedDraft = cache.frontmatter.draft || 1;
                break;
            }
        }
    }

    // If not inferred, prompt for story
    if (!selectedStory) {
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
            if (!selectedStory) { await abort("Story selection cancelled."); return; }

            // Find the story file to read active_draft
            const storyFile = storyFiles.find(file => {
                const cache = app.metadataCache.getFileCache(file);
                return cache.frontmatter.story_title === selectedStory;
            });
            const storyCache = app.metadataCache.getFileCache(storyFile);
            selectedDraft = storyCache?.frontmatter?.draft || 1;
        } else {
            selectedStory = await tp.system.prompt("No existing stories found. Enter story title:");
            if (!selectedStory) { await abort("Story selection cancelled."); return; }
            selectedDraft = 1;
        }
    }

    // Discover available drafts for this story
    const storyPath = `Story/${selectedStory}`;
    const allFolders = app.vault.getAllFolders();
    const draftFolders = allFolders
        .filter(f => f.path.startsWith(storyPath + "/Draft "))
        .map(f => {
            const match = f.path.match(/Draft (\d+)$/);
            return match ? parseInt(match[1]) : null;
        })
        .filter(n => n !== null)
        .sort((a, b) => a - b);

    if (draftFolders.length > 1) {
        // Multiple drafts exist — offer selection, default to active_draft
        const draftLabels = draftFolders.map(n => `Draft ${n}${n === selectedDraft ? " (active)" : ""}`);
        const chosen = await tp.system.suggester(draftLabels, draftFolders);
        if (chosen === null || chosen === undefined) { await abort("Draft selection cancelled."); return; }
        selectedDraft = chosen;
    } else if (draftFolders.length === 1) {
        selectedDraft = draftFolders[0];
    }
    // If no draft folders exist yet, keep selectedDraft as-is (defaults to 1)

    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to the draft folder
const targetFolder = `Story/${selectedStory}/Draft ${selectedDraft}`;
await tp.file.move(`${targetFolder}/${title}`);

// Auto-increment chapter-number based on existing chapters in this draft
let nextChapter = 1;
const draftFiles = app.vault.getFiles()
    .filter(f => f.path.startsWith(targetFolder + "/") && f.path !== tp.config.target_file.path);
for (const f of draftFiles) {
    const cache = app.metadataCache.getFileCache(f);
    const num = cache?.frontmatter?.["chapter-number"];
    if (num != null) {
        const intPart = parseInt(num.toString().split('.')[0], 10);
        if (!isNaN(intPart) && intPart >= nextChapter) {
            nextChapter = intPart + 1;
        }
    }
}
const chapterNumber = nextChapter;

// Toggle focus mode if not already active
if (!document.body.classList.contains("focus-mode")) {
    app.commands.executeCommandById("obsidian-focus-mode:toggle-focus-mode");
}
_%>
---
tags:
  - Chapter
story_title: <% selectedStory %>
draft: <% selectedDraft %>
chapter-number: <% chapterNumber %>
status: WIP
pov:
chapter_outline:
related:
involves_world:
cssclasses:
  - lk-page
obsidianUIMode: edit
---
