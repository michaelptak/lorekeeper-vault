<%*
// Get all template files in T_Notes folder
const notesTemplateFiles = app.vault.getFiles()
    .filter(file => file.path.startsWith("Templates/T_Notes/") && file.name.endsWith(".md"))
    .map(file => ({
        name: file.name.replace("Template_Notes_", "").replace(".md", ""),
        path: file.path
    }));

if (notesTemplateFiles.length > 0) {
    // Create display names and file paths for suggester
    const displayNames = notesTemplateFiles.map(template => template.name);
    const templatePaths = notesTemplateFiles.map(template => template.path);
    
    // Let user select from available notes templates
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
    new Notice("No notes templates found in Templates/T_Notes/", 5000);
}
_%>