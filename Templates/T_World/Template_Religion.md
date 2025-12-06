---
tags:
  - Religion
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
> #### Religious Characteristics
>  |
> ---|---|
> **Belief Type** | `INPUT[BeliefType][:belief_type]` |
> **Influence Level** | `INPUT[InfluenceLevel][:influence_level]` |
> **Organizational Structure** | `INPUT[OrganizationalStructure][:organizational_structure]` |
>
> #### Deities & Leadership
>  |
> ---|---|
> **Deities** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):deities]` |
> **Religious Leaders** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):religious_leaders]` |
>
> #### Beliefs & Concepts
>  |
> ---|---|
> **Core Concepts** | `INPUT[inlineListSuggester(optionQuery(#concept AND !"Templates"), useLinks(partial)):core_concepts]` |
>
> #### Practice & Sacred Elements
>  |
> ---|---|
> **Practiced By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #country or #organization AND !"Templates"), useLinks(partial)):practiced_by]` |
> **Holy Sites** | `INPUT[inlineListSuggester(optionQuery(#poi or #settlement or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):holy_sites]` |
> **Sacred Objects** | `INPUT[inlineListSuggester(optionQuery(#object AND !"Templates"), useLinks(partial)):sacred_objects]` |
> **Sacred Texts** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):sacred_texts]` |
>
> #### Relationships
>  |
> ---|---|
> **Associated Magic** | `INPUT[inlineListSuggester(optionQuery(#magic AND !"Templates"), useLinks(partial)):associated_magic]` |
> **Rival Religions** | `INPUT[inlineListSuggester(optionQuery(#religion AND !"Templates"), useLinks(partial)):rival_religions]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Religion.base|All Religions]] | [[Home]]
>
> [[#Overview]] • [[#Beliefs & Teachings|Beliefs]] • [[#Practices & Rituals|Practices]] • [[#Organization & Leadership|Organization]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Belief Type</span> `VIEW[{belief_type}]`
>
> <span class="label">Influence</span> `VIEW[{influence_level}]`
>
> <span class="label">Structure</span> `VIEW[{organizational_structure}]`
>
> <div class="section">Practice</div>
>
> <span class="label">Deities</span> `VIEW[{deities}][link]`
>
> <span class="label">Practiced By</span> `VIEW[{practiced_by}][link]`

## Overview
Brief description of this religion and its significance in the world.

## Beliefs & Teachings
Core doctrines, cosmology, creation myths, afterlife concepts, and theological principles.

## Practices & Rituals
How followers worship, ceremonies, holidays, daily practices, and sacred traditions.

## Organization & Leadership
Religious hierarchy (if any), role of clergy, how the faith is structured and governed.

## Story Notes
How this religion appears in your narratives or influences characters and conflicts.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Religion Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Religion folder
const targetFolder = "World/Religion";
await tp.file.move(`${targetFolder}/${title}`);
_%>