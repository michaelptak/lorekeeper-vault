---
tags:
  - Ancestry
status:
art: Assets/Cards/card-concept.jpg
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Homeland** | `INPUT[inlineListSuggester(optionQuery(#Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):homeland]` |
> **Languages** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):languages]` |
> **Parent Ancestry** | `INPUT[inlineListSuggester(optionQuery(#Ancestry AND !"Templates" AND !"Archive"), useLinks(partial)):parent_ancestry]` |
> **Notable Members** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):notable_members]` |
> **Associated Deities** | `INPUT[inlineListSuggester(optionQuery(#Character or #Religion AND !"Templates" AND !"Archive"), useLinks(partial)):associated_deities]` |
> **Art Forms** | `INPUT[inlineListSuggester(optionQuery(#Art AND !"Templates" AND !"Archive"), useLinks(partial)):art_forms]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Ancestry|All Ancestry]] | [[Home]]

# **Elves**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Homeland</span> `VIEW[{homeland}][link]`
>
> <span class="label">Languages</span> `VIEW[{languages}][link]`
>
> <span class="label">Parent Ancestry</span> `VIEW[{parent_ancestry}][link]`
>
> <span class="label">Notable Members</span> `VIEW[{notable_members}][link]`
>
> <span class="label">Associated Deities</span> `VIEW[{associated_deities}][link]`
>
> <span class="label">Art Forms</span> `VIEW[{art_forms}][link]`

## Overview

## Physical Traits

## Culture & Customs

## History & Origins

## Story Notes
