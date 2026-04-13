---
tags:
  - POI
status:
art:
locations:
jurisdiction:
controlled_by:
discovered_by:
related:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Geography AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):controlled_by]` |
> **Discovered By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):discovered_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[POI|All POIs]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter POI Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/POI";
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
> <span class="label">Location</span> \`VIEW[{locations}][link]\`
>
> <span class="label">Jurisdiction</span> \`VIEW[{jurisdiction}][link]\`
>
> <span class="label">Controlled By</span> \`VIEW[{controlled_by}][link]\`
>
> <span class="label">Discovered By</span> \`VIEW[{discovered_by}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Description\n\n## History & Significance\n\n## Story Notes\n";
}
_%>

