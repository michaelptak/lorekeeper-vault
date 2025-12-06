---
tags:
  - Country
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
> #### National Characteristics
>  |
> ---|---|
> **Government** | `INPUT[Government][:government]` |
> **Size** | `INPUT[Size][:size]` |
> **Wealth Level** | `INPUT[WealthLevel][:wealth_level]` |
> **Stability** | `INPUT[Stability][:stability]` |
> **Military Power** | `INPUT[MilitaryPower][:military_power]` |
>
> #### Leadership & Settlements
>  |
> ---|---|
> **Capital** | `INPUT[inlineListSuggester(optionQuery(#settlement AND !"Templates"), useLinks(partial)):capital]` |
> **Rulers** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):rulers]` |
> **Major Cities** | `INPUT[inlineListSuggester(optionQuery(#settlement AND !"Templates"), useLinks(partial)):major_cities]` |
> **Territory** | `INPUT[inlineListSuggester(optionQuery(#geography AND !"Templates"), useLinks(partial)):territory]` |
>
> #### Economy
>  |
> ---|---|
> **Economy** | `INPUT[inlineListSuggester(optionQuery(#economy AND !"Templates"), useLinks(partial)):economy]` |
>
> #### International Relations
>  |
> ---|---|
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):allies]` |
> **Enemies** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):enemies]` |
> **Vassals** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):vassals]` |
> **Overlord** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):overlord]` |
>
> #### Population & Culture
>  |
> ---|---|
> **Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#ancestry AND !"Templates"), useLinks(partial)):inhabitants]` |
> **Official Religion** | `INPUT[inlineListSuggester(optionQuery(#religion AND !"Templates"), useLinks(partial)):official_religion]` |
> **Languages** | `INPUT[inlineListSuggester(optionQuery(#language AND !"Templates"), useLinks(partial)):languages]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Country.base|All Countries]] | [[Home]]
>
> [[#Overview]] • [[#Geography & Territory|Geography]] • [[#Government & Politics|Government]] • [[#Society & Culture|Society]]
>
> [[#Economy & Military|Economy]] • [[#International Relations|Relations]] • [[#History]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Government</span> `VIEW[{government}]`
>
> <span class="label">Size</span> `VIEW[{size}]`
>
> <span class="label">Wealth</span> `VIEW[{wealth_level}]`
>
> <span class="label">Stability</span> `VIEW[{stability}]`
>
> <span class="label">Military</span> `VIEW[{military_power}]`
>
> <div class="section">Leadership</div>
>
> <span class="label">Capital</span> `VIEW[{capital}][link]`
>
> <span class="label">Rulers</span> `VIEW[{rulers}][link]`

## Overview
Brief description of this country and its place in the world.

## Geography & Territory
Physical lands controlled, major geographic features, climate, and natural resources.

## Government & Politics
How the country is governed, political structure, succession, and internal power dynamics.

## Society & Culture
Who lives here, social structures, cultural values, daily life, and traditions.

## Economy & Military
Economic foundation, trade relationships, military organization, and strategic capabilities.

## International Relations
Diplomatic relationships, alliances, conflicts, and position in regional/global politics.

## History
Founding, major historical events, evolution, and how the nation came to its current state.

## Story Notes
How this country features in your narratives and its role in plot events.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Country Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Country folder
const targetFolder = "World/Country";
await tp.file.move(`${targetFolder}/${title}`);
_%>