---
tags:
  - POI
status:
art: Assets/Cards/card-object.jpg
locations:
  - "[[Volcanic Ash Fields]]"
jurisdiction:
  - "[[Atlantis]]"
controlled_by:
  - "[[A powerful org]]"
discovered_by:
  - "[[Jeff]]"
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Geography AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):controlled_by]` |
> **Discovered By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):discovered_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[POI|All POIs]] | [[Home]]

# **An interesting Large Rock**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Location</span> `VIEW[{locations}][link]`
>
> <span class="label">Jurisdiction</span> `VIEW[{jurisdiction}][link]`
>
> <span class="label">Controlled By</span> `VIEW[{controlled_by}][link]`
>
> <span class="label">Discovered By</span> `VIEW[{discovered_by}][link]`

## Overview

## Description

## History & Significance

## Story Notes
