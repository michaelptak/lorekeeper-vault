---
tags:
  - Magic
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
> #### Magic Characteristics
>  |
> ---|---|
> **Magic Scope** | `INPUT[MagicScope][:magic_scope]` |
> **Magic Type** | `INPUT[MagicType][:magic_type]` |
> **Learning Method** | `INPUT[LearningMethod][:learning_method]` |
> **Societal View** | `INPUT[SocietalView][:societal_view]` |
> **Rarity** | `INPUT[MagicRarity][:rarity]` |
>
> #### Source & Requirements
>  |
> ---|---|
> **Power Source** | `INPUT[inlineListSuggester(optionQuery(#concept or #cosmos or #geography AND !"Templates"), useLinks(partial)):power_source]` |
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#object or #resource or #condition AND !"Templates"), useLinks(partial)):requires]` |
>
> #### Practice & Teaching
>  |
> ---|---|
> **Practiced By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization or #character or #religion AND !"Templates"), useLinks(partial)):practiced_by]` |
> **Taught At** | `INPUT[inlineListSuggester(optionQuery(#organization or #settlement or #poi AND !"Templates"), useLinks(partial)):taught_at]` |
>
> #### Effects & Relations
>  |
> ---|---|
> **Enables** | `INPUT[inlineListSuggester(optionQuery(#object or #magic or #concept AND !"Templates"), useLinks(partial)):enables]` |
> **Countered By** | `INPUT[inlineListSuggester(optionQuery(#magic or #object or #condition AND !"Templates"), useLinks(partial)):countered_by]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Magic.base|All Magic]] | [[Home]]
>
> [[#Overview]] • [[#How It Works]] • [[#Learning & Practice|Practice]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Scope</span> `VIEW[{magic_scope}]`
>
> <span class="label">Type</span> `VIEW[{magic_type}]`
>
> <span class="label">Rarity</span> `VIEW[{rarity}]`
>
> <span class="label">View</span> `VIEW[{societal_view}]`
>
> <div class="section">Practice</div>
>
> <span class="label">Learning</span> `VIEW[{learning_method}]`
>
> <span class="label">Practiced By</span> `VIEW[{practiced_by}][link]`

## Overview
Brief description of this magic system, discipline, spell, or item and its significance.

## How It Works
Mechanisms, principles, power source, requirements, and what makes this magic function.

## Learning & Practice
How it's learned, who can use it, where it's taught, limitations, and dangers.

## Effects & Applications
What this magic does, what it enables, and what can counter or nullify it.

## Story Notes
How this magic appears in your narratives or drives plot developments.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Magic Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Magic folder
const targetFolder = "World/Magic";
await tp.file.move(`${targetFolder}/${title}`);
_%>