---
tags:
  - Character
status: Complete
role: Ally
life_status: Alive
aliases:
  - The Accursed One
age:
art:
---

> [!metadata]- Links
>  |
> ---|---|
> **Art** | `INPUT[imageSuggester(optionQuery("Assets")):art]` |
> **Ancestry** | `INPUT[inlineListSuggester(optionQuery(#Ancestry AND !"Templates" AND !"Archive"), useLinks(partial)):ancestry]` |
> **Organization** | `INPUT[inlineListSuggester(optionQuery(#Organization AND !"Templates" AND !"Archive"), useLinks(partial)):organization]` |
> **Location** | `INPUT[inlineListSuggester(optionQuery(#Settlement or #POI or #Geography or #Country AND !"Templates" AND !"Archive"), useLinks(partial)):location]` |
> **Family** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):family]` |
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):allies]` |
> **Enemies** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates" AND !"Archive"), useLinks(partial)):enemies]` |
> **Owns** | `INPUT[inlineListSuggester(optionQuery(#Object AND !"Templates" AND !"Archive"), useLinks(partial)):owns]` |
> **Knows Magic** | `INPUT[inlineListSuggester(optionQuery(#Magic AND !"Templates" AND !"Archive"), useLinks(partial)):knows_magic]` |
> **Follows Religion** | `INPUT[inlineListSuggester(optionQuery(#Religion AND !"Templates" AND !"Archive"), useLinks(partial)):follows_religion]` |
> **Involved In** | `INPUT[inlineListSuggester(optionQuery(#History AND !"Templates" AND !"Archive"), useLinks(partial)):involved_in]` |
> **Conditions** | `INPUT[inlineListSuggester(optionQuery(#Concept or #Condition AND !"Templates" AND !"Archive"), useLinks(partial)):conditions]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates" AND !"Archive"), useLinks(partial)):related]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Character|All Characters]] | [[Home]]

# **Jeff**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
>
> <div class="section">Details</div>
>
> <span class="label">Aliases</span> `VIEW[{aliases}]`
>
> <span class="label">Age</span> `VIEW[{age}]`
>
> <span class="label">Role</span> `VIEW[{role}]`
>
> <span class="label">Status</span> `VIEW[{life_status}]`
>
> <span class="label">Ancestry</span> `VIEW[{ancestry}][link]`
>
> <span class="label">Organization</span> `VIEW[{organization}][link]`
>
> <span class="label">Location</span> `VIEW[{location}][link]`
>
> <div class="section">Relationships</div>
>
> <span class="label">Family</span> `VIEW[{family}][link]`
>
> <span class="label">Allies</span> `VIEW[{allies}][link]`
>
> <span class="label">Enemies</span> `VIEW[{enemies}][link]`

## Overview

## Appearance

## Personality

## Background

## Abilities & Skills

## Story Notes
