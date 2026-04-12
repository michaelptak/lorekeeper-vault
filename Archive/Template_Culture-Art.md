---
tags:
  - Culture/Art
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
> #### Culture/Art Details
>  |
> ---|---|
> **Art Type** | `INPUT[text(placeholder(visual/performance/literary/musical/craft)):art_type]` |
> **Cultural Focus** | `INPUT[text(placeholder(honor/knowledge/nature/war/trade/magic)):cultural_focus]` |
> **Medium** | `INPUT[text(placeholder(oil painting/epic poetry/bronze casting)):medium]` |
> **Era** | `INPUT[text(placeholder(The Golden Age)):era]` |
> **Vitality** | `INPUT[select(option(Thriving), option(Established), option(Declining), option(Lost), option(Revival)):vitality]` |
>
> #### Cultural Concepts
>  |
> ---|---|
> **Core Concepts** | `INPUT[inlineListSuggester(optionQuery(#concept AND !"Templates"), useLinks(partial)):core_concepts]` |
>
> #### Cultural Connections
>  |
> ---|---|
> **Associated Ancestry** | `INPUT[inlineListSuggester(optionQuery(#ancestry AND !"Templates"), useLinks(partial)):associated_ancestry]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#geography or #settlement or #poi or #country or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
> **Influenced By** | `INPUT[inlineListSuggester(optionQuery(#culture AND !"Templates"), useLinks(partial)):influenced_by]` |
>
> #### Patronage & Practice
>  |
> ---|---|
> **Patron** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):patron]` |
> **Practitioners** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):practitioners]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Culture-Art.base|All Culture/Art]] | [[Home]]
>
> [[#Overview]] • [[#Description & Characteristics|Description]] • [[#Cultural Significance|Significance]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{art_type}]`
>
> <span class="label">Focus</span> `VIEW[{cultural_focus}]`
>
> <span class="label">Medium</span> `VIEW[{medium}]`
>
> <span class="label">Vitality</span> `VIEW[{vitality}]`
>
> <div class="section">Cultural Context</div>
>
> <span class="label">Associated Ancestry</span> `VIEW[{associated_ancestry}][link]`
>
> <span class="label">Era</span> `VIEW[{era}]`
>
> <span class="label">Locations</span> `VIEW[{locations}][link]`

## Overview
Brief description of this art form or cultural practice and what makes it distinctive.

## Description & Characteristics
What does this look/sound/feel like? Key techniques, styles, themes, or distinguishing features.

## History & Development
Origins, evolution, influences, and how it spread or changed over time.

## Cultural Significance
What does this mean to practitioners? Social role, symbolic importance, or practical applications.

## Story Notes
How this art or culture appears in your narratives or shapes character backgrounds.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Culture/Art Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Culture-Art folder
const targetFolder = "World/Culture-Art";
await tp.file.move(`${targetFolder}/${title}`);
_%>