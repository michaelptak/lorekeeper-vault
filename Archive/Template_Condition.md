---
tags:
  - Condition
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
> #### Condition Characteristics
>  |
> ---|---|
> **Condition Type** | `INPUT[ConditionType][:condition_type]` |
> **Origin Type** | `INPUT[OriginType][:origin_type]` |
> **Severity** | `INPUT[Severity][:severity]` |
> **Duration** | `INPUT[Duration][:duration]` |
> **Transmission** | `INPUT[Transmission][:transmission]` |
> **Symptoms** | `INPUT[textArea(placeholder(Describe visible effects and symptoms)):symptoms]` |
>
> #### Cause & Effect
>  |
> ---|---|
> **Caused By** | `INPUT[inlineListSuggester(optionQuery(#magic or #creature or #object or #character or #geography or #cosmos AND !"Templates"), useLinks(partial)):caused_by]` |
> **Affects** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #creature or #flora AND !"Templates"), useLinks(partial)):affects]` |
> **Cured By** | `INPUT[inlineListSuggester(optionQuery(#object or #magic or #character or #technology or #resource AND !"Templates"), useLinks(partial)):cured_by]` |
> **Known Cases** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):known_cases]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Condition.base|All Conditions]] | [[Home]]
>
> [[#Overview]] • [[#Symptoms & Effects]] • [[#Transmission & Spread|Spread]] • [[#Treatment & Cure|Treatment]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{condition_type}]`
>
> <span class="label">Origin</span> `VIEW[{origin_type}]`
>
> <span class="label">Severity</span> `VIEW[{severity}]`
>
> <span class="label">Duration</span> `VIEW[{duration}]`
>
> <div class="section">Spread & Treatment</div>
>
> <span class="label">Transmission</span> `VIEW[{transmission}]`
>
> <span class="label">Affects</span> `VIEW[{affects}][link]`
>
> <span class="label">Cured By</span> `VIEW[{cured_by}][link]`

## Overview
Brief description of this condition and its significance in your world.

## Symptoms & Effects
Physical, mental, and other manifestations. How does it progress? What are the stages?

## Transmission & Spread
How the condition is acquired or transmitted. Risk factors and prevention methods.

## Treatment & Cure
Available treatments, cures, or management strategies. Success rates and accessibility.

## Story Notes
How this condition appears in your narratives or affects characters and plot.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Condition Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Condition folder
const targetFolder = "World/Condition";
await tp.file.move(`${targetFolder}/${title}`);
_%>