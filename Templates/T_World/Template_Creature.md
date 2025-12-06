---
tags:
  - Creature
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
> #### Creature Characteristics
>  |
> ---|---|
> **Creature Type** | `INPUT[CreatureType][:creature_type]` |
> **Intelligence** | `INPUT[Intelligence][:intelligence]` |
> **Temperament** | `INPUT[Temperament][:temperament]` |
> **Rarity** | `INPUT[Rarity][:rarity]` |
> **Diet** | `INPUT[Diet][:diet]` |
> **Size** | `INPUT[Size][:size]` |
>
> #### World Connections
>  |
> ---|---|
> **Habitat** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):habitat]` |
> **Domesticated By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization AND !"Templates"), useLinks(partial)):domesticated_by]` |
> **Produces** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):produces]` |
> **Hunted By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization or #creature AND !"Templates"), useLinks(partial)):hunted_by]` |
> **Preys On** | `INPUT[inlineListSuggester(optionQuery(#creature or #ancestry AND !"Templates"), useLinks(partial)):preys_on]` |
>
> #### Artificial Creation (Optional)
>  |
> ---|---|
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#character or #organization or #technology or #magic AND !"Templates"), useLinks(partial)):created_by]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Creature.base|All Creatures]] | [[Home]]
>
> [[#Overview]] • [[#Physical Description]] • [[#Behavior]] • [[#Habitat & Distribution]]
> 
> [[#Cultural Significance]] • [[#Variants|Variants]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{creature_type}]`
>
> <span class="label">Size</span> `VIEW[{size}]`
>
> <span class="label">Intelligence</span> `VIEW[{intelligence}]`
>
> <span class="label">Temperament</span> `VIEW[{temperament}]`
>
> <div class="section">Ecology</div>
>
> <span class="label">Diet</span> `VIEW[{diet}]`
>
> <span class="label">Rarity</span> `VIEW[{rarity}]`
>
> <span class="label">Habitat</span> `VIEW[{habitat}][link]`

## Overview
Brief description of this creature and its place in the world.

## Physical Description
Appearance, size, distinctive features, and any notable variations.

## Behavior
Natural behaviors, social structures, diet, reproduction, and survival strategies.

## Habitat & Distribution
Where it lives, environmental needs, and geographic range.

## Cultural Significance
How sentient beings interact with this creature. Cultural, economic, or mythological importance.

## Variants
Known subspecies, regional variations, or hybrid forms.

## Story Notes
Narrative considerations for how this creature appears in your stories.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Creature Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Creature folder
const targetFolder = "World/Creature";
await tp.file.move(`${targetFolder}/${title}`);
_%>