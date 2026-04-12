---
tags:
  - Magic
status:
art:
power_source:
practiced_by:
requires:
taught_at:
enables:
countered_by:
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Power Source** | `INPUT[inlineListSuggester(optionQuery(#Concept or #Geography AND !"Templates" AND !"Archive"), useLinks(partial)):power_source]` |
> **Practiced By** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Organization or #Character or #Religion AND !"Templates" AND !"Archive"), useLinks(partial)):practiced_by]` |
> **Requires** | `INPUT[inlineListSuggester(optionQuery(#Object or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):requires]` |
> **Taught At** | `INPUT[inlineListSuggester(optionQuery(#Organization or #Settlement or #POI AND !"Templates" AND !"Archive"), useLinks(partial)):taught_at]` |
> **Enables** | `INPUT[inlineListSuggester(optionQuery(#Object or #Magic or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):enables]` |
> **Countered By** | `INPUT[inlineListSuggester(optionQuery(#Magic or #Object or #Concept or #Technology AND !"Templates" AND !"Archive"), useLinks(partial)):countered_by]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Magic|All Magic]] | [[Home]]

# **We casting spells and shi**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Source & Practice</div>
>
> <span class="label">Power Source</span> `VIEW[{power_source}][link]`
>
> <span class="label">Practiced By</span> `VIEW[{practiced_by}][link]`
>
> <span class="label">Requires</span> `VIEW[{requires}][link]`
>
> <span class="label">Taught At</span> `VIEW[{taught_at}][link]`
>
> <div class="section">Effects</div>
>
> <span class="label">Enables</span> `VIEW[{enables}][link]`
>
> <span class="label">Countered By</span> `VIEW[{countered_by}][link]`

## Overview

## How It Works

## Learning & Practice

## Effects & Applications

## Story Notes
