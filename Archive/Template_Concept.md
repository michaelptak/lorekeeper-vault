---
tags:
  - Concept
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
> #### Concept Properties
>  |
> ---|---|
> **Concept Type** | `INPUT[ConceptType][:concept_type]` |
> **Scope** | `INPUT[ConceptScope][:concept_scope]` |
> **Thematic Importance** | `INPUT[ThematicImportance][:thematic_importance]` |
> **Origin** | `INPUT[ConceptOrigin][:origin]` |
> **Awareness** | `INPUT[Awareness][:awareness]` |
> **Truth Status** | `INPUT[TruthStatus][:truth_status]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Concept.base|All Concepts]] | [[Home]]
>
> [[#Overview]] • [[#How It Works]] • [[#Manifestations]] • [[#Implications]]
# **`=this.file.name`**
> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Concept Details</div>
>
> <span class="label">Type</span> `VIEW[{concept_type}]`
>
> <span class="label">Scope</span> `VIEW[{concept_scope}]`
>
> <span class="label">Importance</span> `VIEW[{thematic_importance}]`
>
> <span class="label">Origin</span> `VIEW[{origin}]`
>
> <span class="label">Awareness</span> `VIEW[{awareness}]`
>
> <span class="label">Truth Status</span> `VIEW[{truth_status}]`

## Overview
Brief description of this concept and what it represents in your world.

## How It Works
Explain the fundamental principles, mechanics, or philosophy of this concept.

## Manifestations
How does this concept appear or express itself in the world? Where can you see it in action?

## Implications
What does this concept mean for your world? How does it affect societies, individuals, or the fundamental nature of reality?

## Story Notes
How this concept fits into your narratives and themes.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Concept Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Concept folder
const targetFolder = "World/Concept";
await tp.file.move(`${targetFolder}/${title}`);
_%>
