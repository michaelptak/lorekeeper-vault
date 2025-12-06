<%*
// Get all template files in T_World folder
const worldTemplateFiles = app.vault.getFiles()
    .filter(file => file.path.startsWith("Templates/T_Story/") && file.name.endsWith(".md"))
    .map(file => ({
        name: file.name.replace("Template_", "").replace(".md", ""),
        path: file.path
    }));

if (worldTemplateFiles.length > 0) {
    // Create display names and file paths for suggester
    const displayNames = worldTemplateFiles.map(template => template.name);
    const templatePaths = worldTemplateFiles.map(template => template.path);
    
    // Let user select from available world templates
    const selectedTemplate = await tp.system.suggester(displayNames, templatePaths);
    
    if (selectedTemplate) {
        // Get the template content and output it
        const templateContent = await tp.file.include(`[[${selectedTemplate}]]`);
        tR += templateContent;
    }
    else {
		// User cancelled - delete the file and abort
        new Notice("Template selection cancelled. File creation aborted.", 5000);
        return;
    }
} else {
    // Fallback if no templates found
    new Notice("No story templates found in Templates/T_Story/", 5000);
}
_%>