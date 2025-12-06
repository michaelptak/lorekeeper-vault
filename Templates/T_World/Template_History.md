---
tags:
  - History
art: Assets/TemplateImg/Placeholder-Generic.jpg
fc-calendar: Gregorian Calendar
aat-render-enabled: true
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
> **Historical Scope** | `INPUT[HistoricalScope][:historical_scope]` |
> **Event Type** | `INPUT[list(placeholder(War/Founding/Disaster/Discovery/Cultural Shift)):event_type]` |
> **Scope** | `INPUT[Scope][:scope]` |
> **Era** | `INPUT[text(placeholder(The Great Convergence)):era]` |
> **Start Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-date]` |
> **End Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-end]` |
> 
> #### Involved Parties
>  |
> ---|---|
> **Characters** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):involved_characters]` |
> **Organizations** | `INPUT[inlineListSuggester(optionQuery(#organization AND !"Templates"), useLinks(partial)):involved_organizations]` |
> **Countries** | `INPUT[inlineListSuggester(optionQuery(#country AND !"Templates"), useLinks(partial)):involved_countries]` |
> **Locations** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):locations]` |
> 
> #### Related Events
>  |
> ---|---|
> **Preceded By** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):preceded_by]` |
> **Led To** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):led_to]` |
> **Concurrent With** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):concurrent_with]` |
> 
> #### Sources & Records
>  |
> ---|---|
> **Primary Sources** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):primary_sources]` |
> **Secondary Accounts** | `INPUT[inlineListSuggester(optionQuery(#lore AND !"Templates"), useLinks(partial)):secondary_sources]` |
> **Archaeological Evidence** | `INPUT[inlineListSuggester(optionQuery(#object or #poi AND !"Templates"), useLinks(partial)):evidence]` |
> 
> #### Calendar & Timeline Integration
>  |
> ---|---|
> **Calendar** | `INPUT[text:fc-calendar]` |
> **Event Category** | `INPUT[text:fc-category]` |
> **Display Name** | `INPUT[text(placeholder(Override event title)):fc-display-name]` |
> **Timeline Image** | `INPUT[text(placeholder([[card-history.jpg]] LINK!)):aat-event-picture]` |
> **Show in Timeline** | `INPUT[toggle:aat-render-enabled]` |
> **Timeline Body** | `INPUT[textArea(placeholder(Custom description for timeline)):aat-event-body]` |
> **Additional Timelines** | `INPUT[list(placeholder(regional-history/political-timeline)):timelines]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[History.base|All History]] | [[Home]]
>
> [[#Overview]] • [[#Background & Causes|Background]] • [[#Timeline]] • [[#Impact & Consequences|Impact]] • [[#Story Notes]]

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

## Overview
Brief description of the historical event or era and its significance in your world.

## Background & Causes
What led up to this event? Underlying tensions, discoveries, or circumstances that made it inevitable or possible.

## Timeline
Key dates, phases, and major milestones. Critical turning points and decisive moments.

## Impact & Consequences
Immediate effects and long-term ramifications. How this event shaped politics, society, culture, or the world itself.

## Story Notes
Narrative considerations for how this historical event affects or appears in your stories.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Historical Event/Era Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to History folder
const targetFolder = "World/History";
await tp.file.move(`${targetFolder}/${title}`);
_%>