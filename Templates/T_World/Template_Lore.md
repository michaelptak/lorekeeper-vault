---
tags:
  - Lore
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
> #### Document Properties
>  |
> ---|---|
> **Document Type** | `INPUT[DocumentType][:document_type]` |
> **Form** | `INPUT[Form][:form]` |
> **Authenticity** | `INPUT[Authenticity][:authenticity]` |
> **Preservation** | `INPUT[Preservation][:preservation]` |
> **Access** | `INPUT[Access][:access]` |
> **Date Written** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-date]` |
>
> #### Authorship & Location
>  |
> ---|---|
> **Author** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):author]` |
> **Commissioned By** | `INPUT[inlineListSuggester(optionQuery(#character or #organization AND !"Templates"), useLinks(partial)):commissioned_by]` |
> **Language** | `INPUT[inlineListSuggester(optionQuery(#language AND !"Templates"), useLinks(partial)):languages]` |
> **Current Location** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #organization AND !"Templates"), useLinks(partial)):current_location]` |
> **Original Location** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi AND !"Templates"), useLinks(partial)):original_location]` |
>
> #### References & Sources
>  |
> ---|---|
> **Mentions** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):mentions]` |
> **Supports** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):supports]` |
> **Contradicts** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):contradicts]` |
>
> #### Calendar & Timeline Integration
>  |
> ---|---|
> **Calendar** | `INPUT[text:fc-calendar]` |
> **Event Category** | `INPUT[text(placeholder(Publication/Discovery/etc.)):fc-category]` |
> **Display Name** | `INPUT[text(placeholder(Override document title)):fc-display-name]` |
> **Timeline Image** | `INPUT[text(placeholder([[document-image.jpg]] LINK!)):aat-event-picture]` |
> **Show in Timeline** | `INPUT[toggle:aat-render-enabled]` |
> **Timeline Body** | `INPUT[textArea(placeholder(Custom description for timeline)):aat-event-body]` |
> **Additional Timelines** | `INPUT[list(placeholder(literary-history/religious-texts)):timelines]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Lore.base|All Lore]] | [[Home]]
>
> [[#Overview]] • [[#Content]] • [[#Context & Significance|Context]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Document Details</div>
>
> <span class="label">Type</span> `VIEW[{document_type}]`
>
> <span class="label">Form</span> `VIEW[{form}]`
>
> <span class="label">Authenticity</span> `VIEW[{authenticity}]`
>
> <span class="label">Preservation</span> `VIEW[{preservation}]`
>
> <span class="label">Access</span> `VIEW[{access}]`
>
> <div class="section">Authorship</div>
>
> <span class="label">Author</span> `VIEW[{author}][link]`
>
> <span class="label">Date Written</span> `VIEW[{fc-date}]`
>
> <span class="label">Language</span> `VIEW[{languages}][link]`
>
> <div class="section">Location</div>
>
> <span class="label">Current Location</span> `VIEW[{current_location}][link]`
>
> <div class="section">References</div>
>
> <span class="label">Mentions</span> `VIEW[{mentions}][link]`

## Overview
Brief description of this document and its significance in your world.

## Content
The actual text, excerpts, or summary of what this document contains.

## Context & Significance
When and why was this created? How reliable is it? What biases might exist? Why does this document matter?

## Story Notes
How this document appears in your narratives or what secrets it might reveal.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Lore Document Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Lore folder
const targetFolder = "World/Lore";
await tp.file.move(`${targetFolder}/${title}`);
_%>