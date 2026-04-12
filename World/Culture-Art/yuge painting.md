---
tags:
  - Art
status:
art: Assets/Cards/card-culture.jpeg
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Associated Ancestry** | `INPUT[inlineListSuggester(optionQuery(#Ancestry AND !"Templates" AND !"Archive"), useLinks(partial)):associated_ancestry]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Influenced By** | `INPUT[inlineListSuggester(optionQuery(#Art AND !"Templates" AND !"Archive"), useLinks(partial)):influenced_by]` |
> **Patron** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):patron]` |
> **Practitioners** | `INPUT[inlineListSuggester(optionQuery(#Character or #Organization AND !"Templates" AND !"Archive"), useLinks(partial)):practitioners]` |
> **Associated Religion** | `INPUT[inlineListSuggester(optionQuery(#Religion AND !"Templates" AND !"Archive"), useLinks(partial)):associated_religion]` |
> **Core Concepts** | `INPUT[inlineListSuggester(optionQuery(#Concept AND !"Templates" AND !"Archive"), useLinks(partial)):core_concepts]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Art|All Art]] | [[Home]]

# **yuge painting**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Associated Ancestry</span> `VIEW[{associated_ancestry}][link]`
>
> <span class="label">Locations</span> `VIEW[{locations}][link]`
>
> <span class="label">Influenced By</span> `VIEW[{influenced_by}][link]`
>
> <span class="label">Patron</span> `VIEW[{patron}][link]`
>
> <span class="label">Practitioners</span> `VIEW[{practitioners}][link]`
>
> <span class="label">Associated Religion</span> `VIEW[{associated_religion}][link]`
>
> <span class="label">Core Concepts</span> `VIEW[{core_concepts}][link]`

## Overview

## Form & Medium

## Cultural Significance

## Notable Works & Practitioners

## Story Notes
