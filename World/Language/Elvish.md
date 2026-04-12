---
tags:
  - Language
status:
art: Assets/Cards/card-history.jpg
spoken_by:
  - "[[Atlantis]]"
locations:
  - "[[Atlantis]]"
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Spoken By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):spoken_by]` |
> **Related Languages** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):related_languages]` |
> **Derived From** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):derived_from]` |
> **Written Works** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):written_works]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Language|All Languages]] | [[Home]]

# **Elvish**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Spoken By</span> `VIEW[{spoken_by}][link]`
>
> <span class="label">Related Languages</span> `VIEW[{related_languages}][link]`
>
> <span class="label">Derived From</span> `VIEW[{derived_from}][link]`
>
> <span class="label">Written Works</span> `VIEW[{written_works}][link]`
>
> <span class="label">Locations</span> `VIEW[{locations}][link]`

## Overview

## Script & Writing System

## Common Words & Naming Conventions

## History & Evolution

## Cultural Significance

## Story Notes
