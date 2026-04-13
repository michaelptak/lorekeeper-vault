<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
let selectedStory;
if (hasNewStoryTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Scene Name");
    
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
        selectedStory = await tp.system.prompt("No existing stories found. Enter story title:");
    }
    
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
// Move file to Scenes folder
const targetFolder = `Story/${selectedStory}/Scenes`;
await tp.file.move(`${targetFolder}/${title}`);
app.commands.executeCommandById("obsidian-focus-mode:toggle-focus-mode");
_%>
---
tags:
  - Scene
story_title: <% selectedStory %>
story_order: 
status: WIP
revisions: 1
pov: 
scene_outline:
related:
involves_world:
cssclasses:
  - lk-page
obsidianUIMode: edit
---