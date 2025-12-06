---
tags:
  - History
status: Complete
related:
historical_scope: Era
event_type:
  - Era
scope: Global
era: The Great Reckoning
involved_characters:
  - "[[Pingus]]"
involved_organizations:
involved_countries:
locations:
fc-calendar: Gregorian Calendar
fc-date: 1000-09-24
fc-end: 1500-09-24
fc-category: ""
fc-display-name:
aat-render-enabled: true
aat-event-body: A time of great change in the world
timelines:
  - world-history
aat-event-picture: "[[card-history.jpg]]"
art: Assets/WorldImg/Character/pingus.jpg
---

> [!metadata]- Meta Data
> #### Core Properties
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> **Art** | `INPUT[imageSuggester(optionQuery("Assets/WorldImg")):art]` |
> 
> #### Historical Details
>  |
> ---|---|
> **Historical Scope** | `INPUT[inlineSelect(option(Event), option(Period), option(Era), option(Recurring)):historical_scope]` |
> **Event Type** | `INPUT[list(placeholder(War/Founding/Disaster/Discovery/Cultural Shift)):event_type]` |
> **Scope** | `INPUT[inlineSelect(option(Local), option(Regional), option(National), option(Continental), option(Global), option(Cosmic)):scope]` |
> **Era** | `INPUT[text(placeholder(The Great Convergence)):era]` |
> **Start Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-date]` |
> **End Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-end]` |
> 
> #### Calendar & Timeline Integration
>  |
> ---|---|
> **Calendar** | `INPUT[text:fc-calendar]` |
> **Event Category** | `INPUT[text:fc-category]` |
> **Display Name** | `INPUT[text(placeholder(Override event title)):fc-display-name]` |
> **Show in Timeline** | `INPUT[toggle:aat-render-enabled]` |
>**Timeline Image** | `INPUT[text(placeholder([[Placeholder-Generic.jpg]])):aat-event-picture]` ||
> **Timeline Body** | `INPUT[textArea(placeholder(Custom description for timeline)):aat-event-body]` |
> **Additional Timelines** | `INPUT[list(placeholder(regional-history/political-timeline)):timelines]` |

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
> 
> <div class="section">Event Details</div>
> 
> <span class="label">Type</span> `VIEW[{event_type}]`
> 
> <span class="label">Scope</span> <span>`VIEW[{historical_scope}]` - `VIEW[{scope}]`</span>
> 
> <span class="label">Era</span> `VIEW[{era}]`
> 
> <span class="label">Start Date</span> `VIEW[{fc-date}]`
> 
> <span class="label">End Date</span> `VIEW[{fc-end}]`
> 
> <div class="section">Involved Parties</div>
> 
> <span class="label">Characters</span> `VIEW[{involved_characters}][link]`
> 
> <span class="label">Organizations</span> `VIEW[{involved_organizations}][link]`
> 
> <span class="label">Countries</span> `VIEW[{involved_countries}][link]`
> 
> <div class="section">Locations</div>
> 
> <span class="label">Locations</span> `VIEW[{locations}][link]`

Quick Nav: [[#Overview]] | [[#Timeline]] | [[#Involved Parties]] | [[#Locations]] | [[#Impact & Consequences]] | [[#Related Events]]

## Overview
Brief description of the historical event or era and its significance in your world.

## Background & Causes
What led up to this event? What were the underlying tensions, discoveries, or circumstances that made this inevitable or possible?

## Timeline
### Key Dates & Phases

| Date/Time | Event | Details |
|-----------|--------|---------|
|           |        |         |
|           |        |         |
|           |        |         |

### Major Milestones
Critical turning points, decisive moments, or key developments during this historical period.

## Involved Parties

| Category | Participants | Role/Contribution |
|----------|-------------|-------------------|
| **Characters** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):involved_characters]` | Key individuals and their roles |
| **Organizations** | `INPUT[inlineListSuggester(optionQuery(#organization AND !"Templates"), useLinks(partial)):involved_organizations]` | Institutional involvement |
| **Countries** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):involved_countries]` | Nations and their participation |

### Detailed Involvement
Expand on the specific roles, motivations, and contributions of the key participants.

## Locations

**Primary Locations:** `INPUT[inlineListSuggester(optionQuery(#geography or #settlement or #poi AND !"Templates"), useLinks(partial)):locations]`

### Geographic Context
How the physical locations influenced or were affected by this historical event.

## Impact & Consequences
### Immediate Effects
What changed immediately as a result of this event?

### Long-term Ramifications
How did this event shape the future? What lasting changes occurred in politics, society, culture, or the world itself?

### Cultural & Social Impact
How did this affect daily life, beliefs, or social structures?

## Related Events

| Connection Type | Event | Relationship |
|----------------|--------|--------------|
| **Predecessor** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):preceded_by]` | Events that led to this |
| **Successor** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):led_to]` | Events this caused |
| **Contemporary** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):concurrent_with]` | Simultaneous events |

### Connections to Other History
How this event connects to or influenced other historical moments in your world.

## Sources & Records

| Source Type | Details |
|-------------|---------|
| **Primary Sources** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):primary_sources]` |
| **Secondary Accounts** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):secondary_sources]` |
| **Archaeological Evidence** | `INPUT[inlineListSuggester(optionQuery(#object or #poi AND !"Templates"), useLinks(partial)):evidence]` |

### Historical Accuracy
Notes on reliability of sources, conflicting accounts, or disputed facts.

## Story Notes
Narrative considerations for how this historical event affects or appears in your stories.

