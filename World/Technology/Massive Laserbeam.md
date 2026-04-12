---
tags:
  - Technology
status:
art: Assets/Cards/card-magic.jpeg
created_by:
  - "[[A powerful org]]"
requires:
  - "[[Something spell]]"
replaces:
  - "[[Massive Laserbeam]]"
enables:
  - "[[Something spell]]"
discovered_at:
  - "[[Volcanic Ash Fields]]"
used_by:
  - "[[Beffrey]]"
documentation:
  - "[[How to Use the Massive Laserbeam]]"
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Created By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Character or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):created_by]` |
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic AND !"Templates" AND !"Archive"), useLinks(partial)):requires]` |
> **Replaces** | `INPUT[inlineListSuggester(optionQuery(#Technology AND !"Templates" AND !"Archive"), useLinks(partial)):replaces]` |
> **Enables** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic or #Concept AND !"Templates" AND !"Archive"), useLinks(partial)):enables]` |
> **Discovered At** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Country or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):discovered_at]` |
> **Used By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Character or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):used_by]` |
> **Documentation** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):documentation]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Technology|All Technology]] | [[Home]]

# **Massive Laserbeam**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Origin</div>
>
> <span class="label">Created By</span> `VIEW[{created_by}][link]`
>
> <span class="label">Discovered At</span> `VIEW[{discovered_at}][link]`
>
> <span class="label">Documentation</span> `VIEW[{documentation}][link]`
>
> <div class="section">Usage</div>
>
> <span class="label">Used By</span> `VIEW[{used_by}][link]`
>
> <span class="label">Requires</span> `VIEW[{requires}][link]`
>
> <span class="label">Enables</span> `VIEW[{enables}][link]`
>
> <span class="label">Replaces</span> `VIEW[{replaces}][link]`

## Overview

## How It Works

## Development & Use

## Story Notes
