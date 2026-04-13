<%*
// Get all existing Story notes
const storyFiles = app.vault.getFiles()
    .filter(file => {
        const cache = app.metadataCache.getFileCache(file);
        return cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title;
    });

if (storyFiles.length === 0) {
    new Notice("No stories found. Create a story first.", 5000);
    return;
}

// Create arrays for suggester
const storyTitles = storyFiles.map(file => {
    const cache = app.metadataCache.getFileCache(file);
    return cache.frontmatter.story_title;
});

// Let user select from existing stories
const selectedStory = await tp.system.suggester(storyTitles, storyTitles);

if (!selectedStory) {
    new Notice("Story selection cancelled. File creation aborted.", 5000);
    return;
}

// Store selected story for the note template to pick up
window._lk_story = selectedStory;

// Get all template files in T_Notes folder
const notesTemplateFiles = app.vault.getFiles()
    .filter(file => file.path.startsWith("Templates/T_Notes/") && file.name.endsWith(".md"))
    .map(file => ({
        name: file.name.replace("Template_Notes_", "").replace(".md", ""),
        path: file.path
    }));

if (notesTemplateFiles.length > 0) {
    const displayNames = notesTemplateFiles.map(template => template.name);
    const templatePaths = notesTemplateFiles.map(template => template.path);

    const selectedTemplate = await tp.system.suggester(displayNames, templatePaths);

    if (selectedTemplate) {
        const templateContent = await tp.file.include(`[[${selectedTemplate}]]`);
        tR += templateContent;
    } else {
        delete window._lk_story;
        new Notice("Template selection cancelled. File creation aborted.", 5000);
        return;
    }
} else {
    delete window._lk_story;
    new Notice("No notes templates found in Templates/T_Notes/", 5000);
}
_%>
