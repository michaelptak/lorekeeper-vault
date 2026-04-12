---
tags:
  - Geography
status:
art: Assets/Cards/medieval-forge.jpg
jurisdiction:
  - "[[Atlantis]]"
controlled_by:
  - "[[A powerful org]]"
notable_features:
  - "[[An interesting Large Rock]]"
associated_with:
  - "[[Paganism]]"
  - "[[Great War]]"
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Jurisdiction** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):jurisdiction]` |
> **Controlled By** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):controlled_by]` |
> **Settlements** | `INPUT[inlineListSuggester(optionQuery(#Settlement AND !"Templates" AND !"Archive"), useLinks(partial)):settlements]` |
> **Notable Features** | `INPUT[inlineListSuggester(optionQuery(#POI AND !"Templates" AND !"Archive"), useLinks(partial)):notable_features]` |
> **Native Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#Ancestry or #Nature AND !"Templates" AND !"Archive"), useLinks(partial)):native_inhabitants]` |
> **Resources** | `INPUT[inlineListSuggester(optionQuery(#Object or #Resource AND !"Templates" AND !"Archive"), useLinks(partial)):resources]` |
> **Associated With** | `INPUT[inlineListSuggester(optionQuery(#Religion or #Magic or #Lore or #History AND !"Templates" AND !"Archive"), useLinks(partial)):associated_with]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Geography|All Geography]] | [[Home]]

# **Volcanic Ash Fields**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Jurisdiction</span> `VIEW[{jurisdiction}][link]`
>
> <span class="label">Controlled By</span> `VIEW[{controlled_by}][link]`
>
> <span class="label">Settlements</span> `VIEW[{settlements}][link]`
>
> <span class="label">Notable Features</span> `VIEW[{notable_features}][link]`
>
> <span class="label">Native Inhabitants</span> `VIEW[{native_inhabitants}][link]`
>
> <span class="label">Resources</span> `VIEW[{resources}][link]`
>
> <span class="label">Associated With</span> `VIEW[{associated_with}][link]`

## Overview

## Physical Description

## Climate & Environment

## Inhabitants & Ecology

## History & Significance

## Story Notes
