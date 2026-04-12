---
tags:
  - Technology
status:
art:
created_by:
requires:
replaces:
enables:
discovered_at:
used_by:
documentation:
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Character or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):created_by]` |
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic AND !"Templates" AND !"Archive"), useLinks(partial)):requires]` |
> **Replaces** | `INPUT[inlineListSuggester(optionQuery(#Technology AND !"Templates" AND !"Archive"), useLinks(partial)):replaces]` |
> **Enables** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):enables]` |
> **Discovered At** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Country or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):discovered_at]` |
> **Used By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Character or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):used_by]` |
> **Documentation** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):documentation]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Technology|All Technology]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Technology Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Technology";
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
> [!statbox]+
> # \`=this.file.name\`
> \`VIEW[!\\[\\[{art}\\]\\]][text(renderMarkdown)]\`
>
> <div class="section">Origin</div>
>
> <span class="label">Created By</span> \`VIEW[{created_by}][link]\`
>
> <span class="label">Discovered At</span> \`VIEW[{discovered_at}][link]\`
>
> <span class="label">Documentation</span> \`VIEW[{documentation}][link]\`
>
> <div class="section">Usage</div>
>
> <span class="label">Used By</span> \`VIEW[{used_by}][link]\`
>
> <span class="label">Requires</span> \`VIEW[{requires}][link]\`
>
> <span class="label">Enables</span> \`VIEW[{enables}][link]\`
>
> <span class="label">Replaces</span> \`VIEW[{replaces}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## How It Works\n\n## Development & Use\n\n## Story Notes\n";
}
_%>

