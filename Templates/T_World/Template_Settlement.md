---
tags:
  - Settlement
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
> #### Settlement Characteristics
>  |
> ---|---|
> **Settlement Size** | `INPUT[SettlementSize][:settlement_size]` |
> **Settlement Type** | `INPUT[SettlementType][:settlement_type]` |
> **Prosperity** | `INPUT[Prosperity][:prosperity]` |
> **Defense** | `INPUT[Defense][:defense]` |
> **Founded Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-date]` |
>
> #### Population & Locations
>  |
> ---|---|
> **Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#ancestry AND !"Templates"), useLinks(partial)):inhabitants]` |
> **Notable Locations** | `INPUT[inlineListSuggester(optionQuery(#poi AND !"Templates"), useLinks(partial)):notable_locations]` |
> **Location** | `INPUT[inlineListSuggester(optionQuery(#geography or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
>
> #### Governance & Control
>  |
> ---|---|
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#organization AND !"Templates"), useLinks(partial)):controlled_by]` |
> **Rulers** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):rulers]` |
> **Founded By** | `INPUT[inlineListSuggester(optionQuery(#character or #organization or #country AND !"Templates"), useLinks(partial)):founded_by]` |
>
> #### Economy & Trade
>  |
> ---|---|
> **Economy** | `INPUT[inlineListSuggester(optionQuery(#economy AND !"Templates"), useLinks(partial)):economy]` |
> **Trade Partners** | `INPUT[inlineListSuggester(optionQuery(#settlement or #country AND !"Templates"), useLinks(partial)):trade_partners]` |
> **Produces** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):produces]` |
> **Imports** | `INPUT[inlineListSuggester(optionQuery(#resource AND !"Templates"), useLinks(partial)):imports]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Settlement.base|All Settlements]] | [[Home]]
>
> [[#Overview]] • [[#Description]] • [[#Population & Culture|Population]] • [[#Economy & Trade|Economy]]
>
> [[#Governance & Politics|Governance]] • [[#History]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Size</span> `VIEW[{settlement_size}]`
>
> <span class="label">Type</span> `VIEW[{settlement_type}]`
>
> <span class="label">Prosperity</span> `VIEW[{prosperity}]`
>
> <span class="label">Defense</span> `VIEW[{defense}]`
>
> <div class="section">Location & Rule</div>
>
> <span class="label">Geography</span> `VIEW[{locations}][link]`
>
> <span class="label">Rulers</span> `VIEW[{rulers}][link]`
>
> <span class="label">Jurisdiction</span> `VIEW[{jurisdiction}][link]`

## Overview
Brief description of this settlement and its role in the world.

## Description
Physical layout, architecture, atmosphere, and distinctive features of the settlement.

## Population & Culture
Who lives here, cultural characteristics, social dynamics, and daily life.

## Economy & Trade
Economic foundation, major industries, trade relationships, and resources.

## Governance & Politics
How the settlement is ruled, political structure, and key power players.

## History
When and why it was founded, major events, and how it evolved over time.

## Story Notes
How this settlement features in your narratives and its role in plot events.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Settlement Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Settlement folder
const targetFolder = "World/Settlement";
await tp.file.move(`${targetFolder}/${title}`);
_%>