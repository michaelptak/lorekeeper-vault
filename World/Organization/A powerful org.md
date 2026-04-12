---
tags:
  - Organization
status:
art: Assets/Cards/card-economy.jpg
headquarters:
  - "[[Atlantis]]"
leader:
  - "[[Jeff]]"
members:
  - "[[Beffrey]]"
founded_by:
  - "[[Matilda]]"
allies:
  - "[[Atlantis]]"
rivals:
  - "[[Atlantis]]"
operates_in:
  - "[[Volcanic Ash Fields]]"
controls:
  - "[[An interesting Large Rock]]"
associated_religion:
  - "[[Paganism]]"
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Headquarters** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):headquarters]` |
> **Leader** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):leader]` |
> **Members** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):members]` |
> **Founded By** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):founded_by]` |
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):allies]` |
> **Rivals** | `INPUT[inlineListSuggester(optionQuery(#Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):rivals]` |
> **Operates In** | `INPUT[inlineListSuggester(optionQuery(#Country or #Settlement or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):operates_in]` |
> **Controls** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Object AND !"Templates" AND !"Archive"), useLinks(partial)):controls]` |
> **Associated Religion** | `INPUT[inlineListSuggester(optionQuery(#Religion AND !"Templates" AND !"Archive"), useLinks(partial)):associated_religion]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Organization|All Organizations]] | [[Home]]

# **A powerful org**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Leadership</div>
>
> <span class="label">Leader</span> `VIEW[{leader}][link]`
>
> <span class="label">Founded By</span> `VIEW[{founded_by}][link]`
>
> <span class="label">Headquarters</span> `VIEW[{headquarters}][link]`
>
> <div class="section">Operations</div>
>
> <span class="label">Operates In</span> `VIEW[{operates_in}][link]`
>
> <span class="label">Controls</span> `VIEW[{controls}][link]`
>
> <span class="label">Religion</span> `VIEW[{associated_religion}][link]`
>
> <div class="section">Relations</div>
>
> <span class="label">Allies</span> `VIEW[{allies}][link]`
>
> <span class="label">Rivals</span> `VIEW[{rivals}][link]`

## Overview

## Structure & Hierarchy

## Purpose & Activities

## History & Development

## Story Notes
