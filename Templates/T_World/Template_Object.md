---
tags:
  - Object
status:
rarity:
art:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Creator** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):creator]` |
> **Current Owner** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):current_owner]` |
> **Located At** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):located_at]` |
> **Made From** | `INPUT[inlineListSuggester(optionQuery(#Object AND !"Templates" AND !"Archive"), useLinks(partial)):made_from]` |
> **Required For** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):required_for]` |
> **Associated With** | `INPUT[inlineListSuggester(optionQuery(#History or #Character or #Religion or #Lore or #Magic AND !"Templates" AND !"Archive"), useLinks(partial)):associated_with]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[Object|All Objects]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Object Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Object";
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
> <span class="label">Rarity</span> \`VIEW[{rarity}]\`
>
> <span class="label">Creator</span> \`VIEW[{creator}][link]\`
>
> <span class="label">Current Owner</span> \`VIEW[{current_owner}][link]\`
>
> <span class="label">Located At</span> \`VIEW[{located_at}][link]\`
>
> <span class="label">Made From</span> \`VIEW[{made_from}][link]\`
>
> <span class="label">Required For</span> \`VIEW[{required_for}][link]\`
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
    tR += "\n## Overview\n\n## Physical Description\n\n## Origin & History\n\n## Properties & Uses\n\n## Cultural Significance\n\n## Story Notes\n";
}
_%>

