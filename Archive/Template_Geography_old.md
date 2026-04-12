---
tags:
  - Geography
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
> #### Geographic Characteristics
>  |
> ---|---|
> **Terrain** | `INPUT[Terrain][:terrain]` |
> **Climate** | `INPUT[Climate][:climate]` |
> **Habitability** | `INPUT[Habitability][:habitability]` |
> **Region Type** | `INPUT[RegionType][:region_type]` |
> **Size** | `INPUT[GeoSize][:size]` |
>
> #### Locations & Features
>  |
> ---|---|
> **Notable Features** | `INPUT[inlineListSuggester(optionQuery(#poi AND !"Templates"), useLinks(partial)):notable_features]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#geography AND !"Templates"), useLinks(partial)):locations]` |
> **Settlements** | `INPUT[inlineListSuggester(optionQuery(#settlement AND !"Templates"), useLinks(partial)):settlements]` |
>
> #### Political & Control
>  |
> ---|---|
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#organization AND !"Templates"), useLinks(partial)):controlled_by]` |
> **Contested By** | `INPUT[inlineListSuggester(optionQuery(#country or #organization AND !"Templates"), useLinks(partial)):contested_by]` |
>
> #### Natural Inhabitants & Resources
>  |
> ---|---|
> **Native Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #creature or #flora AND !"Templates"), useLinks(partial)):native_inhabitants]` |
> **Resources** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):resources]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Geography.base|All Geography]] | [[Home]]
>
> [[#Overview]] • [[#Physical Description]] • [[#Inhabitants]] • [[#Resources & Economy|Resources]]
>
> [[#Political Status|Politics]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{region_type}]`
>
> <span class="label">Terrain</span> `VIEW[{terrain}]`
>
> <span class="label">Climate</span> `VIEW[{climate}]`
>
> <span class="label">Size</span> `VIEW[{size}]`
>
> <span class="label">Habitability</span> `VIEW[{habitability}]`
>
> <div class="section">Political Status</div>
>
> <span class="label">Jurisdiction</span> `VIEW[{jurisdiction}][link]`
>
> <span class="label">Controlled By</span> `VIEW[{controlled_by}][link]`

## Overview
Brief description of this geographic region and its significance in the world.

## Physical Description
Natural terrain, climate patterns, weather, distinctive landmarks, and overall landscape character.

## Inhabitants
Who or what naturally lives here - sentient populations, native creatures, and unique flora.

## Resources & Economy
Natural resources, economic activities, and what makes this region valuable or strategically important.

## Political Status
Territorial control, disputes, strategic significance, and political relationships.

## Story Notes
Narrative considerations, plot significance, and how this location serves your stories.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Geography Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Geography folder
const targetFolder = "World/Geography";
await tp.file.move(`${targetFolder}/${title}`);
_%>