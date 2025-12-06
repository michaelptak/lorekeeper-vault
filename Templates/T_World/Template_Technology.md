---
tags:
  - Technology
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
> #### Technology Characteristics
>  |
> ---|---|
> **Tech Stage** | `INPUT[TechStage][:tech_stage]` |
> **Availability** | `INPUT[Availability][:availability]` |
> **Tech Type** | `INPUT[TechType][:tech_type]` |
> **Complexity** | `INPUT[Complexity][:complexity]` |
>
> #### Development & Discovery
>  |
> ---|---|
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization or #character or #country AND !"Templates"), useLinks(partial)):created_by]` |
> **Discovered At** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #country or #geography or #cosmos AND !"Templates"), useLinks(partial)):discovered_at]` |
> **Used By** | `INPUT[inlineListSuggester(optionQuery(#ancestry or #organization or #character or #country AND !"Templates"), useLinks(partial)):used_by]` |
>
> #### Requirements & Relations
>  |
> ---|---|
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#resource or #magic or #object AND !"Templates"), useLinks(partial)):requires]` |
> **Replaces** | `INPUT[inlineListSuggester(optionQuery(#technology AND !"Templates"), useLinks(partial)):replaces]` |
> **Enables** | `INPUT[inlineListSuggester(optionQuery(#object or #magic or #concept AND !"Templates"), useLinks(partial)):enables]` |
> **Documentation** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):documentation]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Technology.base|All Technology]] | [[Home]]
>
> [[#Overview]] • [[#How It Works]] • [[#Development & Use]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{tech_type}]`
>
> <span class="label">Stage</span> `VIEW[{tech_stage}]`
>
> <span class="label">Complexity</span> `VIEW[{complexity}]`
>
> <span class="label">Availability</span> `VIEW[{availability}]`
>
> <div class="section">Development</div>
>
> <span class="label">Created By</span> `VIEW[{created_by}][link]`
>
> <span class="label">Used By</span> `VIEW[{used_by}][link]`

## Overview
Brief description of this technology and its significance in your world.

## How It Works
Mechanisms, principles, and processes that make this technology function.

## Development & Use
Who created it, where it was developed, what it requires, who uses it, and what it enables.

## Story Notes
How this technology appears in your narratives or drives plot developments.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Technology Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Technology folder
const targetFolder = "World/Technology";
await tp.file.move(`${targetFolder}/${title}`);
_%>