<%*
// Get all template files in T_Meta folder
const metaTemplateFiles = app.vault.getFiles()
    .filter(file => file.path.startsWith("Templates/T_Meta/") && file.name.endsWith(".md"))
    .map(file => ({
        name: file.name.replace("Template_Meta_", "").replace(".md", ""),
        path: file.path
    }));

if (metaTemplateFiles.length > 0) {
    // Create display names and file paths for suggester
    const displayNames = metaTemplateFiles.map(template => template.name);
    const templatePaths = metaTemplateFiles.map(template => template.path);
    
    // Let user select from available meta templates
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
    new Notice("No meta templates found in Templates/T_Meta/", 5000);
}
_%>