---
tags:
  - Ancestry
status:
art:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Homeland** | `INPUT[inlineListSuggester(optionQuery(#Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):homeland]` |
> **Languages** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):languages]` |
> **Parent Ancestry** | `INPUT[inlineListSuggester(optionQuery(#Ancestry AND !"Templates" AND !"Archive"), useLinks(partial)):parent_ancestry]` |
> **Notable Members** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):notable_members]` |
> **Associated Deities** | `INPUT[inlineListSuggester(optionQuery(#Character or #Religion AND !"Templates" AND !"Archive"), useLinks(partial)):associated_deities]` |
> **Art Forms** | `INPUT[inlineListSuggester(optionQuery(#Art AND !"Templates" AND !"Archive"), useLinks(partial)):art_forms]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[Ancestry|All Ancestry]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Ancestry Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Ancestry";
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
> <span class="label">Homeland</span> \`VIEW[{homeland}][link]\`
>
> <span class="label">Languages</span> \`VIEW[{languages}][link]\`
>
> <span class="label">Parent Ancestry</span> \`VIEW[{parent_ancestry}][link]\`
>
> <span class="label">Notable Members</span> \`VIEW[{notable_members}][link]\`
>
> <span class="label">Associated Deities</span> \`VIEW[{associated_deities}][link]\`
>
> <span class="label">Art Forms</span> \`VIEW[{art_forms}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Physical Traits\n\n## Culture & Customs\n\n## History & Origins\n\n## Story Notes\n";
}
_%>

