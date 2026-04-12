---
tags:
  - Country
status:
art: Assets/Cards/card-country.jpeg
rulers:
  - "[[Jeff]]"
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Capital** | `INPUT[inlineListSuggester(optionQuery(#Settlement AND !"Templates" AND !"Archive"), useLinks(partial)):capital]` |
> **Rulers** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):rulers]` |
> **Major Cities** | `INPUT[inlineListSuggester(optionQuery(#Settlement AND !"Templates" AND !"Archive"), useLinks(partial)):major_cities]` |
> **Territory** | `INPUT[inlineListSuggester(optionQuery(#Geography AND !"Templates" AND !"Archive"), useLinks(partial)):territory]` |
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):allies]` |
> **Enemies** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):enemies]` |
> **Vassals** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):vassals]` |
> **Overlord** | `INPUT[inlineListSuggester(optionQuery(#Country AND !"Templates" AND !"Archive"), useLinks(partial)):overlord]` |
> **Inhabitants** | `INPUT[inlineListSuggester(optionQuery(#Ancestry AND !"Templates" AND !"Archive"), useLinks(partial)):inhabitants]` |
> **Official Religion** | `INPUT[inlineListSuggester(optionQuery(#Religion AND !"Templates" AND !"Archive"), useLinks(partial)):official_religion]` |
> **Languages** | `INPUT[inlineListSuggester(optionQuery(#Language AND !"Templates" AND !"Archive"), useLinks(partial)):languages]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Country|All Countries]] | [[Home]]

# **Atlantis**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Leadership</div>
>
> <span class="label">Capital</span> `VIEW[{capital}][link]`
>
> <span class="label">Rulers</span> `VIEW[{rulers}][link]`
>
> <div class="section">People & Culture</div>
>
> <span class="label">Inhabitants</span> `VIEW[{inhabitants}][link]`
>
> <span class="label">Religion</span> `VIEW[{official_religion}][link]`
>
> <span class="label">Languages</span> `VIEW[{languages}][link]`
>
> <div class="section">Relations</div>
>
> <span class="label">Allies</span> `VIEW[{allies}][link]`
>
> <span class="label">Enemies</span> `VIEW[{enemies}][link]`

## Overview

## Geography & Territory

## Government & Politics

## Society & Culture

## Economy & Military

## International Relations

## History

## Story Notes
