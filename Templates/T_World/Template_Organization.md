---
tags:
  - Organization
status:
art:
headquarters:
leader:
members:
founded_by:
allies:
rivals:
operates_in:
controls:
associated_religion:
related:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Headquarters** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):headquarters]` |
> **Leader** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):leader]` |
> **Members** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):members]` |
> **Founded By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):founded_by]` |
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):allies]` |
> **Rivals** | `INPUT[inlineListSuggester(optionQuery(#Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):rivals]` |
> **Operates In** | `INPUT[inlineListSuggester(optionQuery(#Country or #Settlement or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):operates_in]` |
> **Controls** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Object AND !"Templates" AND !"Archive"), useLinks(partial)):controls]` |
> **Associated Religion** | `INPUT[inlineListSuggester(optionQuery(#Religion AND !"Templates" AND !"Archive"), useLinks(partial)):associated_religion]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[Organization|All Organizations]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Organization Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Organization";
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
> <div class="section">Leadership</div>
>
> <span class="label">Leader</span> \`VIEW[{leader}][link]\`
>
> <span class="label">Founded By</span> \`VIEW[{founded_by}][link]\`
>
> <span class="label">Headquarters</span> \`VIEW[{headquarters}][link]\`
>
> <div class="section">Operations</div>
>
> <span class="label">Operates In</span> \`VIEW[{operates_in}][link]\`
>
> <span class="label">Controls</span> \`VIEW[{controls}][link]\`
>
> <span class="label">Religion</span> \`VIEW[{associated_religion}][link]\`
>
> <div class="section">Relations</div>
>
> <span class="label">Allies</span> \`VIEW[{allies}][link]\`
>
> <span class="label">Rivals</span> \`VIEW[{rivals}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Structure & Hierarchy\n\n## Purpose & Activities\n\n## History & Development\n\n## Story Notes\n";
}
_%>

