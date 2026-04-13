---
tags:
  - History
status:
historical_scope:
art:
involved_characters:
involved_organizations:
involved_countries:
locations:
preceded_by:
led_to:
concurrent_with:
sources:
related:
---

> [!lk-metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Involved Characters** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):involved_characters]` |
> **Involved Organizations** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):involved_organizations]` |
> **Involved Countries** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):involved_countries]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Preceded By** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):preceded_by]` |
> **Led To** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):led_to]` |
> **Concurrent With** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):concurrent_with]` |
> **Sources** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):sources]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!lk-navbar]+ Navigation
> [[History|All History]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter History Entry Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/History";
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
> <div class="section">Involved</div>
>
> <span class="label">Characters</span> \`VIEW[{involved_characters}][link]\`
>
> <span class="label">Organizations</span> \`VIEW[{involved_organizations}][link]\`
>
> <span class="label">Countries</span> \`VIEW[{involved_countries}][link]\`
>
> <span class="label">Locations</span> \`VIEW[{locations}][link]\`
>
> <div class="section">Timeline</div>
>
> <span class="label">Preceded By</span> \`VIEW[{preceded_by}][link]\`
>
> <span class="label">Led To</span> \`VIEW[{led_to}][link]\`
>
> <span class="label">Concurrent With</span> \`VIEW[{concurrent_with}][link]\`
>
> <span class="label">Sources</span> \`VIEW[{sources}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Key Figures\n\n## Causes\n\n## Events\n\n## Consequences\n\n## Legacy\n\n## Story Notes\n";
}
_%>

