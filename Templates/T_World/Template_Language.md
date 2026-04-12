---
tags:
  - Language
status:
art:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Spoken By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):spoken_by]` |
> **Related Languages** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):related_languages]` |
> **Derived From** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):derived_from]` |
> **Written Works** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):written_works]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Language|All Languages]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Language Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Language";
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
> <span class="label">Spoken By</span> \`VIEW[{spoken_by}][link]\`
>
> <span class="label">Related Languages</span> \`VIEW[{related_languages}][link]\`
>
> <span class="label">Derived From</span> \`VIEW[{derived_from}][link]\`
>
> <span class="label">Written Works</span> \`VIEW[{written_works}][link]\`
>
> <span class="label">Locations</span> \`VIEW[{locations}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Script & Writing System\n\n## Common Words & Naming Conventions\n\n## History & Evolution\n\n## Cultural Significance\n\n## Story Notes\n";
}
_%>

