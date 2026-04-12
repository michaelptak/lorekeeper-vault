---
tags:
  - Politics
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
> #### Political Characteristics
>  |
> ---|---|
> **Political Type** | `INPUT[PoliticalType][:political_type]` |
> **Political Status** | `INPUT[PoliticalStatus][:political_status]` |
> **Scope** | `INPUT[Scope][:scope]` |
> **Outcome** | `INPUT[Outcome][:outcome]` |
>
> #### Parties & Relations
>  |
> ---|---|
> **Parties Involved** | `INPUT[inlineListSuggester(optionQuery(#country or #organization or #character AND !"Templates"), useLinks(partial)):parties_involved]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
> **Supersedes** | `INPUT[inlineListSuggester(optionQuery(#politics AND !"Templates"), useLinks(partial)):supersedes]` |
> **Led To** | `INPUT[inlineListSuggester(optionQuery(#politics or #history AND !"Templates"), useLinks(partial)):led_to]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Politics.base|All Politics]] | [[Home]]
>
> [[#Overview]] • [[#Details & Terms]] • [[#Impact & Consequences|Impact]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{political_type}]`
>
> <span class="label">Status</span> `VIEW[{political_status}]`
>
> <span class="label">Scope</span> `VIEW[{scope}]`
>
> <span class="label">Outcome</span> `VIEW[{outcome}]`
>
> <div class="section">Involved Parties</div>
>
> <span class="label">Parties</span> `VIEW[{parties_involved}][link]`

## Overview
Brief description of this political event, law, treaty, or policy.

## Details & Terms
Specific provisions, terms, conditions, or key elements of this political matter.

## Impact & Consequences
What resulted from this? Who was affected? What changed politically, economically, or socially?

## Story Notes
How this political element appears in your narratives or drives conflicts.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Politics Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Politics folder
const targetFolder = "World/Politics";
await tp.file.move(`${targetFolder}/${title}`);
_%>