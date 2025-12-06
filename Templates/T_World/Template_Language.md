---
tags:
  - Language
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
> #### Language Characteristics
>  |
> ---|---|
> **Usage** | `INPUT[Usage][:usage]` |
> **Script** | `INPUT[Script][:script]` |
> **Family** | `INPUT[text(placeholder(Elvish languages/Dwarven dialects)):family]` |
> **Prevalence** | `INPUT[Prevalence][:prevalence]` |
>
> #### Speakers & Distribution
>  |
> ---|---|
> **Spoken By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization or #country AND !"Templates"), useLinks(partial)):spoken_by]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
>
> #### Linguistic Relations
>  |
> ---|---|
> **Derived From** | `INPUT[inlineListSuggester(optionQuery(#language AND !"Templates"), useLinks(partial)):derived_from]` |
> **Related Languages** | `INPUT[inlineListSuggester(optionQuery(#language AND !"Templates"), useLinks(partial)):related_languages]` |
> **Written Works** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):written_works]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Language.base|All Languages]] | [[Home]]
>
> [[#Overview]] • [[#Linguistic Features]] • [[#Usage & Distribution|Distribution]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Usage</span> `VIEW[{usage}]`
>
> <span class="label">Script</span> `VIEW[{script}]`
>
> <span class="label">Family</span> `VIEW[{family}]`
>
> <span class="label">Prevalence</span> `VIEW[{prevalence}]`
>
> <div class="section">Speakers</div>
>
> <span class="label">Spoken By</span> `VIEW[{spoken_by}][link]`
>
> <span class="label">Locations</span> `VIEW[{locations}][link]`

## Overview
Brief description of this language and its role in the world.

## Linguistic Features
Key characteristics - sounds, grammar quirks, unique features, or flavor. Keep it simple unless you're doing deep conlang work.

## Usage & Distribution
Who speaks it, where it's spoken, how it's used (daily life, ceremonies, trade, etc.).

## History & Evolution
Origins, how it developed, relationship to other languages.

## Story Notes
How this language appears in your narratives - phrases, naming conventions, cultural significance.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Language Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Language folder
const targetFolder = "World/Language";
await tp.file.move(`${targetFolder}/${title}`);
_%>