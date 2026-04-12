---
tags:
  - Resource
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
> #### Resource Characteristics
>  |
> ---|---|
> **Resource Type** | `INPUT[ResourceType][:resource_type]` |
> **Rarity** | `INPUT[ResourceRarity][:rarity]` |
> **Renewability** | `INPUT[Renewability][:renewability]` |
> **State** | `INPUT[State][:state]` |
> **Value** | `INPUT[Value][:value]` |
> **Primary Use** | `INPUT[PrimaryUse][:primary_use]` |
>
> #### Source & Distribution
>  |
> ---|---|
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
> **Source** | `INPUT[inlineListSuggester(optionQuery(#geography or #creature or #flora or #poi or #cosmos AND !"Templates"), useLinks(partial)):source]` |
> **Harvested By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization AND !"Templates"), useLinks(partial)):harvested_by]` |
> **Traded Via** | `INPUT[inlineListSuggester(optionQuery(#economy AND !"Templates"), useLinks(partial)):traded_via]` |
>
> #### Usage & Applications
>  |
> ---|---|
> **Required For** | `INPUT[inlineListSuggester(optionQuery(#object or #magic or #technology AND !"Templates"), useLinks(partial)):required_for]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Resource.base|All Resources]] | [[Home]]
>
> [[#Overview]] • [[#Properties & Characteristics|Properties]] • [[#Extraction & Processing]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{resource_type}]`
>
> <span class="label">State</span> `VIEW[{state}]`
>
> <span class="label">Rarity</span> `VIEW[{rarity}]`
>
> <span class="label">Value</span> `VIEW[{value}]`
>
> <div class="section">Availability</div>
>
> <span class="label">Renewability</span> `VIEW[{renewability}]`
>
> <span class="label">Primary Use</span> `VIEW[{primary_use}]`
>
> <span class="label">Locations</span> `VIEW[{locations}][link]`

## Overview
Brief description of this resource and its importance in your world.

## Properties & Characteristics
Physical properties, appearance, how to identify it, and what makes it unique or valuable.

## Extraction & Processing
How it's obtained, who harvests it, processing methods, and any challenges or dangers in acquiring it.

## Uses & Applications
What this resource is used for and what depends on it.

## Story Notes
How this resource factors into your narratives - scarcity conflicts, economic importance, plot devices.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Resource Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Resource folder
const targetFolder = "World/Resource";
await tp.file.move(`${targetFolder}/${title}`);
_%>