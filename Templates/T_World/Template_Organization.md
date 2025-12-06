---
tags:
  - Organization
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
> #### Organization Characteristics
>  |
> ---|---|
> **Org Type** | `INPUT[OrgType][:org_type]` |
> **Scope** | `INPUT[Scope][:scope]` |
> **Secrecy** | `INPUT[Secrecy][:secrecy]` |
> **Size** | `INPUT[OrgSize][:size]` |
> **Influence** | `INPUT[Influence][:influence]` |
>
> #### Leadership & Membership
>  |
> ---|---|
> **Leader** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):leader]` |
> **Members** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):members]` |
> **Founded By** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):founded_by]` |
>
> #### Location & Operations
>  |
> ---|---|
> **Headquarters** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):headquarters]` |
> **Operates In** | `INPUT[inlineListSuggester(optionQuery(#country or #settlement or #geography or #cosmos AND !"Templates"), useLinks(partial)):operates_in]` |
> **Controls** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #resource AND !"Templates"), useLinks(partial)):controls]` |
>
> #### Relationships
>  |
> ---|---|
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#organization or #country AND !"Templates"), useLinks(partial)):allies]` |
> **Rivals** | `INPUT[inlineListSuggester(optionQuery(#organization or #country AND !"Templates"), useLinks(partial)):rivals]` |
> **Associated Religion** | `INPUT[inlineListSuggester(optionQuery(#religion AND !"Templates"), useLinks(partial)):associated_religion]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Organization.base|All Organizations]] | [[Home]]
>
> [[#Overview]] • [[#Structure & Hierarchy|Structure]] • [[#Purpose & Activities|Purpose]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Basic Information</div>
>
> <span class="label">Type</span> `VIEW[{org_type}]`
>
> <span class="label">Scope</span> `VIEW[{scope}]`
>
> <span class="label">Secrecy</span> `VIEW[{secrecy}]`
>
> <span class="label">Size</span> `VIEW[{size}]`
>
> <span class="label">Influence</span> `VIEW[{influence}]`
>
> <div class="section">Leadership</div>
>
> <span class="label">Leader</span> `VIEW[{leader}][link]`
>
> <span class="label">Headquarters</span> `VIEW[{headquarters}][link]`

## Overview
Brief description of this organization and its role in the world.

## Structure & Hierarchy
How the organization is structured, ranks, membership requirements, and internal governance.

## Purpose & Activities
What the organization does, its goals, methods, and operations.

## History & Development
When and why it was founded, major events, and how it evolved over time.

## Story Notes
How this organization appears in your narratives or influences plot events.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Organization Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Organization folder
const targetFolder = "World/Organization";
await tp.file.move(`${targetFolder}/${title}`);
_%>