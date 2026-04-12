---
tags:
  - History
status:
historical_scope:
art: Assets/Cards/card-condition.jpg
involved_characters:
  - "[[Jeff]]"
involved_organizations:
involved_countries:
  - "[[Atlantis]]"
locations:
preceded_by:
led_to:
concurrent_with:
sources:
related:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Involved Characters** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):involved_characters]` |
> **Involved Organizations** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):involved_organizations]` |
> **Involved Countries** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):involved_countries]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):locations]` |
> **Preceded By** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):preceded_by]` |
> **Led To** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):led_to]` |
> **Concurrent With** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):concurrent_with]` |
> **Sources** | `INPUT[inlineListSuggester(optionQuery(#Lore AND !"Templates" AND !"Archive"), useLinks(partial)):sources]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[History|All History]] | [[Home]]

# **Great War**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Involved</div>
>
> <span class="label">Characters</span> `VIEW[{involved_characters}][link]`
>
> <span class="label">Organizations</span> `VIEW[{involved_organizations}][link]`
>
> <span class="label">Countries</span> `VIEW[{involved_countries}][link]`
>
> <span class="label">Locations</span> `VIEW[{locations}][link]`
>
> <div class="section">Timeline</div>
>
> <span class="label">Preceded By</span> `VIEW[{preceded_by}][link]`
>
> <span class="label">Led To</span> `VIEW[{led_to}][link]`
>
> <span class="label">Concurrent With</span> `VIEW[{concurrent_with}][link]`
>
> <span class="label">Sources</span> `VIEW[{sources}][link]`

## Overview

## Key Figures

## Causes

## Events

## Consequences

## Legacy

## Story Notes
