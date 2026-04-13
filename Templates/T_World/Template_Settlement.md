---
tags:
  - Settlement
status:
art:
inhabitants:
notable_sites:
locations:
jurisdiction:
controlled_by:
rulers:
founded_by:
trade_partners:
resources:
related:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#Ancestry AND !"Templates" AND !"Archive"), useLinks(partial)):inhabitants]` |
> **Notable Sites** | `INPUT[inlineListSuggester(optionQuery(#POI AND !"Templates" AND !"Archive"), useLinks(partial)):notable_sites]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Geography AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):controlled_by]` |
> **Rulers** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):rulers]` |
> **Founded By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):founded_by]` |
> **Trade Partners** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):trade_partners]` |
> **Resources** | `INPUT[inlineListSuggester(optionQuery(#Object AND !"Templates" AND !"Archive"), useLinks(partial)):resources]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[Settlement|All Settlements]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Settlement Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Settlement";
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
> <div class="section">Location & Rule</div>
>
> <span class="label">Location</span> \`VIEW[{locations}][link]\`
>
> <span class="label">Jurisdiction</span> \`VIEW[{jurisdiction}][link]\`
>
> <span class="label">Rulers</span> \`VIEW[{rulers}][link]\`
>
> <span class="label">Controlled By</span> \`VIEW[{controlled_by}][link]\`
>
> <div class="section">People & Trade</div>
>
> <span class="label">Inhabitants</span> \`VIEW[{inhabitants}][link]\`
>
> <span class="label">Trade Partners</span> \`VIEW[{trade_partners}][link]\`
>
> <span class="label">Resources</span> \`VIEW[{resources}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Description\n\n## Population & Culture\n\n## Economy & Trade\n\n## Governance\n\n## History\n\n## Story Notes\n";
}
_%>

