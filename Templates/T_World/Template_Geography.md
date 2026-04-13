---
tags:
  - Geography
status:
art:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):controlled_by]` |
> **Settlements** | `INPUT[inlineListSuggester(optionQuery(#Settlement AND !"Templates" AND !"Archive"), useLinks(partial)):settlements]` |
> **Notable Features** | `INPUT[inlineListSuggester(optionQuery(#POI AND !"Templates" AND !"Archive"), useLinks(partial)):notable_features]` |
> **Native Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Nature AND !"Templates" AND !"Archive"), useLinks(partial)):native_inhabitants]` |
> **Resources** | `INPUT[inlineListSuggester(optionQuery(#Object AND !"Templates" AND !"Archive"), useLinks(partial)):resources]` |
> **Associated With** | `INPUT[inlineListSuggester(optionQuery(#Religion or #Magic or #Lore or #History AND !"Templates" AND !"Archive"), useLinks(partial)):associated_with]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[Geography|All Geography]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Geography Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Geography";
await tp.file.move(`${targetFolder}/${title}`);

tR += `# **${title}**\n`;

// Include infobox? (ALT+T -> Infobox_* to add later)
const infobox = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include infobox?"
);

if (infobox) {
    tR += `
> [!lk-infobox]+
> # \`=this.file.name\`
> \`VIEW[!\\[\\[{art}\\]\\]][text(renderMarkdown)]\`
>
> <div class="section">Details</div>
>
> <span class="label">Jurisdiction</span> \`VIEW[{jurisdiction}][link]\`
>
> <span class="label">Controlled By</span> \`VIEW[{controlled_by}][link]\`
>
> <span class="label">Settlements</span> \`VIEW[{settlements}][link]\`
>
> <span class="label">Notable Features</span> \`VIEW[{notable_features}][link]\`
>
> <span class="label">Native Inhabitants</span> \`VIEW[{native_inhabitants}][link]\`
>
> <span class="label">Resources</span> \`VIEW[{resources}][link]\`
>
> <span class="label">Associated With</span> \`VIEW[{associated_with}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Physical Description\n\n## Climate & Environment\n\n## Inhabitants & Ecology\n\n## History & Significance\n\n## Story Notes\n";
}
_%>

