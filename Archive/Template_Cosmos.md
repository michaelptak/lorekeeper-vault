---
tags:
  - Cosmos
art: Assets/TemplateImg/Placeholder-Generic.jpg
---

> [!metadata]- Meta Data
> #### Core Properties
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> **Art** | `INPUT[imageSuggester(optionQuery("Assets/WorldImg")):art]` |
>
> #### Cosmos Properties
>  |
> ---|---|
> **Cosmic Type** | `INPUT[CosmicType][:cosmic_type]` |
> **Visibility** | `INPUT[Visibility][:visibility]` |
> **Significance** | `INPUT[Significance][:significance]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
> **Associated With** | `INPUT[inlineListSuggester(optionQuery(#religion or #magic or #lore AND !"Templates"), useLinks(partial)):associated_with]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Cosmos.base|All Cosmos]] | [[Home]]
>
> [[#Overview]] • [[#Appearance]] • [[#Cultural Significance]] • [[#Story Notes]]
# **`=this.file.name`**
> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Cosmic Details</div>
>
> <span class="label">Type</span> `VIEW[{cosmic_type}]`
>
> <span class="label">Visibility</span> `VIEW[{visibility}]`
>
> <span class="label">Significance</span> `VIEW[{significance}]`
>
> <span class="label">Best Viewed From</span> `VIEW[{locations}][link]`
>
> <span class="label">Associated With</span> `VIEW[{associated_with}][link]`

## Overview
Brief description of this celestial body or phenomenon and what it is.

## Appearance
Describe what this looks like in the sky. Color, size, patterns, movement, etc.

## Cultural Significance
How do different cultures view or use this celestial feature? What stories, beliefs, or practical applications surround it?

## Story Notes
How this cosmic element fits into your narratives and world events.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Cosmos Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Cosmos folder
const targetFolder = "World/Cosmos";
await tp.file.move(`${targetFolder}/${title}`);
_%>
