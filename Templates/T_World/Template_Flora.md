---
tags:
  - Flora
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
> #### Flora Characteristics
>  |
> ---|---|
> **Plant Type** | `INPUT[PlantType][:plant_type]` |
> **Rarity** | `INPUT[FloraRarity][:rarity]` |
> **Properties** | `INPUT[FloraProperties][:properties]` |
> **Size** | `INPUT[FloraSize][:size]` |
> **Lifecycle** | `INPUT[Lifecycle][:lifecycle]` |
>
> #### World Connections
>  |
> ---|---|
> **Habitat** | `INPUT[inlineListSuggester(optionQuery(#geography or #settlement or #cosmos or #poi or #country AND !"Templates"), useLinks(partial)):habitat]` |
> **Cultivated By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization AND !"Templates"), useLinks(partial)):cultivated_by]` |
> **Produces** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):produces]` |
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#resource or #condition AND !"Templates"), useLinks(partial)):requires]` |
> **Consumed By** | `INPUT[inlineListSuggester(optionQuery(#creature or #ancestry AND !"Templates"), useLinks(partial)):consumed_by]` |
>
> #### Artificial Creation (Optional)
>  |
> ---|---|
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#character or #organization or #magic or #technology AND !"Templates"), useLinks(partial)):created_by]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Flora.base|All Flora]] | [[Home]]
>
> [[#Overview]] • [[#Physical Description]] • [[#Growth & Ecology]] • [[#Properties & Uses]]
>
> [[#Habitat & Distribution]] • [[#Cultural Significance]] • [[#Variants|Variants]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{plant_type}]`
>
> <span class="label">Size</span> `VIEW[{size}]`
>
> <span class="label">Properties</span> `VIEW[{properties}]`
>
> <span class="label">Lifecycle</span> `VIEW[{lifecycle}]`
>
> <div class="section">Ecology</div>
>
> <span class="label">Rarity</span> `VIEW[{rarity}]`
>
> <span class="label">Habitat</span> `VIEW[{habitat}][link]`

## Overview
Brief description of this plant and its place in the world.

## Physical Description
Appearance, size, distinctive features, and growth stages.

## Growth & Ecology
Growth patterns, reproduction, environmental requirements, and natural threats.

## Properties & Uses
Natural properties, magical characteristics, medicinal/alchemical uses, or culinary applications.

## Habitat & Distribution
Where it grows naturally or is cultivated. Geographic range and seasonal availability.

## Cultural Significance
How sentient beings interact with this plant. Cultural, economic, or symbolic importance.

## Variants
Known subspecies, regional variations, or cultivated varieties.

## Story Notes
Narrative considerations for how this plant appears in your stories.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Flora Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Flora folder
const targetFolder = "World/Flora";
await tp.file.move(`${targetFolder}/${title}`);
_%>