---
tags:
  - Religion
status:
art:
deities:
practiced_by:
holy_sites:
sacred_objects:
sacred_texts:
religious_leaders:
core_concepts:
associated_magic:
rival_religions:
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Deities** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):deities]` |
> **Practiced By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Country or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):practiced_by]` |
> **Holy Sites** | `INPUT[inlineListSuggester(optionQuery(#POI or #Settlement or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):holy_sites]` |
> **Sacred Objects** | `INPUT[inlineListSuggester(optionQuery(#Object AND !"Templates" AND !"Archive"), useLinks(partial)):sacred_objects]` |
> **Sacred Texts** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):sacred_texts]` |
> **Religious Leaders** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):religious_leaders]` |
> **Core Concepts** | `INPUT[inlineListSuggester(optionQuery(#Concept AND !"Templates" AND !"Archive"), useLinks(partial)):core_concepts]` |
> **Associated Magic** | `INPUT[inlineListSuggester(optionQuery(#Magic AND !"Templates" AND !"Archive"), useLinks(partial)):associated_magic]` |
> **Rival Religions** | `INPUT[inlineListSuggester(optionQuery(#Religion AND !"Templates" AND !"Archive"), useLinks(partial)):rival_religions]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Religion|All Religions]] | [[Home]]

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Religion Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "World/Religion";
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
> <div class="section">Divine</div>
>
> <span class="label">Deities</span> \`VIEW[{deities}][link]\`
>
> <span class="label">Core Concepts</span> \`VIEW[{core_concepts}][link]\`
>
> <span class="label">Associated Magic</span> \`VIEW[{associated_magic}][link]\`
>
> <div class="section">Practice</div>
>
> <span class="label">Practiced By</span> \`VIEW[{practiced_by}][link]\`
>
> <span class="label">Religious Leaders</span> \`VIEW[{religious_leaders}][link]\`
>
> <span class="label">Holy Sites</span> \`VIEW[{holy_sites}][link]\`
>
> <span class="label">Sacred Objects</span> \`VIEW[{sacred_objects}][link]\`
>
> <span class="label">Sacred Texts</span> \`VIEW[{sacred_texts}][link]\`
>
> <div class="section">Relations</div>
>
> <span class="label">Rival Religions</span> \`VIEW[{rival_religions}][link]\`
`;
}

const outline = await tp.system.suggester(
    ["Yes", "No"],
    [true, false],
    false,
    "Include outline?"
);

if (outline) {
    tR += "\n## Overview\n\n## Beliefs & Teachings\n\n## Practices & Rituals\n\n## Organization & Leadership\n\n## Story Notes\n";
}
_%>

