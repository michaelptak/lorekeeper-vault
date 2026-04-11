<%*
const infoboxFiles = app.vault.getFiles()
    .filter(file => file.path.startsWith("Templates/T_Infobox/") && file.name.endsWith(".md"))
    .map(file => ({
        name: file.name.replace("Infobox_", "").replace(".md", ""),
        path: file.path
    }));

if (infoboxFiles.length > 0) {
    const displayNames = infoboxFiles.map(t => t.name);
    const templatePaths = infoboxFiles.map(t => t.path);

    const selectedTemplate = await tp.system.suggester(displayNames, templatePaths);

    if (selectedTemplate) {
        const templateContent = await tp.file.include(`[[${selectedTemplate}]]`);
        tR += templateContent;
    } else {
        new Notice("Infobox selection cancelled.", 3000);
    }
} else {
    new Notice("No infobox templates found in Templates/T_Infobox/", 5000);
}
_%>
