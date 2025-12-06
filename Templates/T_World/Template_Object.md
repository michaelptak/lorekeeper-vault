---
tags:
  - Object
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
> #### Object Characteristics
>  |
> ---|---|
> **Object Type** | `INPUT[text(placeholder(weapon/tool/jewelry/relic/clothing)):object_type]` |
> **Rarity** | `INPUT[ObjectRarity][:rarity]` |
> **Condition** | `INPUT[ObjectCondition][:condition]` |
> **Significance** | `INPUT[Significance][:significance]` |
>
> #### Creation & Materials
>  |
> ---|---|
> **Creator** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):creator]` |
> **Made From** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):made_from]` |
> **Enchanted By** | `INPUT[inlineListSuggester(optionQuery(#character or #magic AND !"Templates"), useLinks(partial)):enchanted_by]` |
> **Created At** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):created_at]` |
>
> #### Ownership & Location
>  |
> ---|---|
> **Original Owner** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):original_owner]` |
> **Current Owner** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):current_owner]` |
> **Currently Located** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):currently_located]` |
>
> #### Historical Context
>  |
> ---|---|
> **Associated With** | `INPUT[inlineListSuggester(optionQuery(#history or #character AND !"Templates"), useLinks(partial)):associated_with]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Object.base|All Objects]] | [[Home]]
>
> [[#Overview]] • [[#Description]] • [[#History & Provenance|History]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{object_type}]`
>
> <span class="label">Rarity</span> `VIEW[{rarity}]`
>
> <span class="label">Condition</span> `VIEW[{condition}]`
>
> <span class="label">Significance</span> `VIEW[{significance}]`
>
> <div class="section">Ownership</div>
>
> <span class="label">Creator</span> `VIEW[{creator}][link]`
>
> <span class="label">Current Owner</span> `VIEW[{current_owner}][link]`
>
> <span class="label">Location</span> `VIEW[{currently_located}][link]`

## Overview
Brief description of this object and what makes it notable.

## Description
Physical appearance, materials, craftsmanship, size, and distinguishing features.

## Properties & Abilities
Special properties, enchantments, or unique characteristics this object possesses.

## History & Provenance
Who created it, why, its journey through different owners, and significant events involving it.

## Story Notes
How this object appears in your narratives or its role in plot events.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Object Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Object folder
const targetFolder = "World/Object";
await tp.file.move(`${targetFolder}/${title}`);
_%>