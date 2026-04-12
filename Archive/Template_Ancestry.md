---
tags:
  - Ancestry
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
> #### Ancestry Characteristics
>  |
> ---|---|
> **Lifespan** | `INPUT[Lifespan][:lifespan]` |
> **Build** | `INPUT[Build][:build]` |
> **Origin** | `INPUT[Origin][:origin]` |
>
> #### World Connections
>  |
> ---|---|
> **Homeland** | `INPUT[inlineListSuggester(optionQuery(#geography or #country or #cosmos AND !"Templates"), useLinks(partial)):homeland]` |
> **Languages** | `INPUT[inlineListSuggester(optionQuery(#language AND !"Templates"), useLinks(partial)):languages]` |
> **Parent Ancestry** | `INPUT[inlineListSuggester(optionQuery(#ancestry AND !"Templates"), useLinks(partial)):parent_ancestry]` |
> **Notable Members** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):notable_members]` |
> **Associated Deities** | `INPUT[inlineListSuggester(optionQuery(#religion or #character AND !"Templates"), useLinks(partial)):associated_deities]` |
>
> #### Cultural Elements
>  |
> ---|---|
> **Art Forms** | `INPUT[inlineListSuggester(optionQuery(#culture AND !"Templates"), useLinks(partial)):art_forms]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Ancestry.base|All Ancestries]] | [[Home]]
>
> [[#Overview]] • [[#Physical Traits]] • [[#Culture & Society]] • [[#Abilities & Traits]] •[[#Relations with Others|Relations]] • [[#History & Origins|History]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Lifespan</span> `VIEW[{lifespan}]`
>
> <span class="label">Build</span> `VIEW[{build}]`
>
> <span class="label">Origin</span> `VIEW[{origin}]`
>
> <div class="section">World Details</div>
>
> <span class="label">Homeland</span> `VIEW[{homeland}][link]`
>
> <span class="label">Languages</span> `VIEW[{languages}][link]`
>
> <span class="label">Parent Ancestry</span> `VIEW[{parent_ancestry}][link]`

## Overview
Brief description of this ancestry and their place in the world.

## Physical Traits
Typical appearance, distinguishing features, size, lifespan, and how aging affects them.

## Culture & Society
Values, traditions, social structures, homeland influence, and typical occupations or roles.

## Abilities & Traits
Natural abilities, common talents, and any limitations or vulnerabilities.

## Relations with Others
How this ancestry interacts with other ancestries. Historical context and current dynamics.

## History & Origins
How they came to be, major migrations, and key historical events that shaped them.

## Variants & Subraces
Known subraces, regional variants, or hybrid ancestries.

## Story Notes
Narrative considerations for this ancestry in your stories.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Ancestry Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Ancestry folder
const targetFolder = "World/Ancestry";
await tp.file.move(`${targetFolder}/${title}`);
_%>