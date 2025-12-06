---
tags:
  - POI
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
> #### POI Characteristics
>  |
> ---|---|
> **POI Type** | `INPUT[POIType][:poi_type]` |
> **Condition** | `INPUT[Condition][:condition]` |
> **Access** | `INPUT[POIAccess][:access]` |
> **Significance** | `INPUT[POISignificance][:significance]` |
>
> #### Location & Control
>  |
> ---|---|
> **Location** | `INPUT[inlineListSuggester(optionQuery(#geography or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#organization AND !"Templates"), useLinks(partial)):controlled_by]` |
> **Discovered By** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):discovered_by]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[POI.base|All POIs]] | [[Home]]
>
> [[#Overview]] • [[#Description]] • [[#History & Significance|History]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{poi_type}]`
>
> <span class="label">Condition</span> `VIEW[{condition}]`
>
> <span class="label">Access</span> `VIEW[{access}]`
>
> <span class="label">Significance</span> `VIEW[{significance}]`
>
> <div class="section">Location</div>
>
> <span class="label">Location</span> `VIEW[{locations}][link]`
>
> <span class="label">Controlled By</span> `VIEW[{controlled_by}][link]`

## Overview
Brief description of this point of interest and what makes it notable.

## Description
Physical appearance, layout, distinctive features, and current state.

## History & Significance
How this place came to be, major events that occurred here, and why it matters.

## Story Notes
How this location appears in your narratives or its role in plot events.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter POI Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to POI folder
const targetFolder = "World/POI";
await tp.file.move(`${targetFolder}/${title}`);
_%>