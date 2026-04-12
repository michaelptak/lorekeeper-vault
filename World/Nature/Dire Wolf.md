---
tags:
  - Nature
status:
rarity:
art:
habitat:
  - "[[Volcanic Ash Fields]]"
raised_by:
  - "[[A powerful org]]"
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Habitat** | `INPUT[inlineListSuggester(optionQuery(#Geography or #Settlement or #POI AND !"Templates" AND !"Archive"), useLinks(partial)):habitat]` |
> **Produces** | `INPUT[inlineListSuggester(optionQuery(#Object AND !"Templates" AND !"Archive"), useLinks(partial)):produces]` |
> **Raised By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):raised_by]` |
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization or #Magic AND !"Templates" AND !"Archive"), useLinks(partial)):created_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Nature|All Nature]] | [[Home]]

# **Dire Wolf**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Rarity</span> `VIEW[{rarity}]`
>
> <span class="label">Habitat</span> `VIEW[{habitat}][link]`
>
> <span class="label">Produces</span> `VIEW[{produces}][link]`
>
> <span class="label">Raised By</span> `VIEW[{raised_by}][link]`
>
> <span class="label">Created By</span> `VIEW[{created_by}][link]`

## Overview

## Physical Description

## Behavior & Ecology

## Habitat & Distribution

## Cultural Significance

## Story Notes
