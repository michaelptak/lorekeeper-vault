---
tags:
  - Magic
status:
art:
power_source:
practiced_by:
requires:
taught_at:
enables:
countered_by:
related:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Power Source** | `INPUT[inlineListSuggester(optionQuery(#Concept or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):power_source]` |
> **Practiced By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Character or #Religion AND !"Templates" AND !"Archive"), useLinks(partial)):practiced_by]` |
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#Object or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):requires]` |
> **Taught At** | `INPUT[inlineListSuggester(optionQuery(#Organization or #Settlement or #POI AND !"Templates" AND !"Archive"), useLinks(partial)):taught_at]` |
> **Enables** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):enables]` |
> **Countered By** | `INPUT[inlineListSuggester(optionQuery(#Magic or #Object or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):countered_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[Magic|All Magic]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Magic Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Magic";
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
> <div class="section">Source & Practice</div>
>
> <span class="label">Power Source</span> \`VIEW[{power_source}][link]\`
>
> <span class="label">Practiced By</span> \`VIEW[{practiced_by}][link]\`
>
> <span class="label">Requires</span> \`VIEW[{requires}][link]\`
>
> <span class="label">Taught At</span> \`VIEW[{taught_at}][link]\`
>
> <div class="section">Effects</div>
>
> <span class="label">Enables</span> \`VIEW[{enables}][link]\`
>
> <span class="label">Countered By</span> \`VIEW[{countered_by}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## How It Works\n\n## Learning & Practice\n\n## Effects & Applications\n\n## Story Notes\n";
}
_%>

