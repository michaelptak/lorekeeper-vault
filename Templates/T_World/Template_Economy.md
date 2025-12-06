---
tags:
  - Economy
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
> #### Economic Characteristics
>  |
> ---|---|
> **Economic Type** | `INPUT[EconomicType][:economic_type]` |
> **Stability** | `INPUT[EconomicStability][:stability]` |
> **Scope** | `INPUT[Scope][:scope]` |
> **Economic Model** | `INPUT[EconomicModel][:economic_model]` |
>
> #### Trade & Resources
>  |
> ---|---|
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#organization or #country AND !"Templates"), useLinks(partial)):controlled_by]` |
> **Trades In** | `INPUT[inlineListSuggester(optionQuery(#resource or #object AND !"Templates"), useLinks(partial)):trades_in]` |
> **Commodity** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):commodity]` |
> **Connects** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):connects]` |
> **Competitors** | `INPUT[inlineListSuggester(optionQuery(#economy AND !"Templates"), useLinks(partial)):competitors]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Economy.base|All Economy]] | [[Home]]
>
> [[#Overview]] • [[#Structure & Function|Structure]] • [[#Impact & Significance|Impact]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{economic_type}]`
>
> <span class="label">Model</span> `VIEW[{economic_model}]`
>
> <span class="label">Stability</span> `VIEW[{stability}]`
>
> <span class="label">Scope</span> `VIEW[{scope}]`
>
> <div class="section">Control & Trade</div>
>
> <span class="label">Controlled By</span> `VIEW[{controlled_by}][link]`
>
> <span class="label">Connects</span> `VIEW[{connects}][link]`

## Overview
Brief description of this economic system, trade route, market, or industry.

## Structure & Function
How it operates, key mechanisms, infrastructure, and what makes it work.

## Impact & Significance
Economic importance, who benefits, regional or global influence, and dependencies.

## Story Notes
How this economic element appears in your narratives or drives plot conflicts.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Economy Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Economy folder
const targetFolder = "World/Economy";
await tp.file.move(`${targetFolder}/${title}`);
_%>