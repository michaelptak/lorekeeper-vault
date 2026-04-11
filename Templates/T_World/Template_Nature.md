---
tags:
  - Nature
status:
rarity:
art:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Habitat** | `INPUT[inlineListSuggester(optionQuery(#Geography or #Settlement or #POI AND !"Templates"), useLinks(partial)):habitat]` |
> **Produces** | `INPUT[inlineListSuggester(optionQuery(#Resource or #Object AND !"Templates"), useLinks(partial)):produces]` |
> **Raised By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization AND !"Templates"), useLinks(partial)):raised_by]` |
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization or #Magic AND !"Templates"), useLinks(partial)):created_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Nature|All Nature]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Nature Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Nature";
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
> <span class="label">Rarity</span> \`VIEW[{rarity}]\`
>
> <span class="label">Habitat</span> \`VIEW[{habitat}][link]\`
>
> <span class="label">Produces</span> \`VIEW[{produces}][link]\`
>
> <span class="label">Raised By</span> \`VIEW[{raised_by}][link]\`
>
> <span class="label">Created By</span> \`VIEW[{created_by}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Physical Description\n\n## Behavior & Ecology\n\n## Habitat & Distribution\n\n## Cultural Significance\n\n## Story Notes\n";
}
_%>

