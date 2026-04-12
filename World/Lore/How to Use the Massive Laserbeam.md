---
tags:
  - Lore
status:
document_type:
art:
author:
  - "[[Jeff]]"
commissioned_by:
  - "[[A powerful org]]"
languages:
  - "[[Elvish]]"
current_location:
mentions:
  - "[[Massive Laserbeam]]"
contradicts:
supports:
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Author** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):author]` |
> **Commissioned By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):commissioned_by]` |
> **Languages** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):languages]` |
> **Current Location** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):current_location]` |
> **Mentions** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):mentions]` |
> **Contradicts** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):contradicts]` |
> **Supports** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):supports]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Lore|All Lore]] | [[Home]]

# **How to Use the Massive Laserbeam**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Author</span> `VIEW[{author}][link]`
>
> <span class="label">Commissioned By</span> `VIEW[{commissioned_by}][link]`
>
> <span class="label">Languages</span> `VIEW[{languages}][link]`
>
> <span class="label">Current Location</span> `VIEW[{current_location}][link]`
>
> <div class="section">References</div>
>
> <span class="label">Mentions</span> `VIEW[{mentions}][link]`
>
> <span class="label">Contradicts</span> `VIEW[{contradicts}][link]`
>
> <span class="label">Supports</span> `VIEW[{supports}][link]`

## Summary

## Contents

## Origin & Provenance

## Significance

## Story Notes
