---
tags:
  - Concept
status:
art:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Associated With** | `INPUT[inlineListSuggester(optionQuery(#Religion or #Magic or #Country or #Art AND !"Templates" AND !"Archive"), useLinks(partial)):associated_with]` |
> **Affects** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Nature or #Character AND !"Templates" AND !"Archive"), useLinks(partial)):affects]` |
> **Caused By** | `INPUT[inlineListSuggester(optionQuery(#Magic or #Object or #Character or #Nature AND !"Templates" AND !"Archive"), useLinks(partial)):caused_by]` |
> **Cured By** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic or #Character or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):cured_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Concept|All Concepts]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Concept Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Concept";
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
> <div class="section">Details</div>
>
> <span class="label">Associated With</span> \`VIEW[{associated_with}][link]\`
>
> <span class="label">Affects</span> \`VIEW[{affects}][link]\`
>
> <span class="label">Caused By</span> \`VIEW[{caused_by}][link]\`
>
> <span class="label">Cured By</span> \`VIEW[{cured_by}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## How It Works\n\n## Impact & Consequences\n\n## Cultural Perception\n\n## Story Notes\n";
}
_%>

