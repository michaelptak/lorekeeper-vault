---
tags:
  - Character
art: Assets/TemplateImg/Placeholder-Character.jpg
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
> #### Identity
>  |
> ---|---|
> **Aliases** | `INPUT[list(placeholder(Nicknames/Titles/etc.)):aliases]` |
> **Gender** | `INPUT[Gender][:gender]` |
> **Age** | `INPUT[Age][:age]` |
> **Date of Birth** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-date]` |
> **Date of Death** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-end]` |
> **Ancestry** | `INPUT[inlineListSuggester(optionQuery(#ancestry AND !"Templates"), useLinks(partial)):ancestry]` |
> **Life Status** | `INPUT[select(option(Alive), option(Dead), option(Unknown), option(Undead)):life_status]` |
> 
> #### Social Position
>  |
> ---|---|
> **Role** | `INPUT[list(placeholder(Protagonist/Ally/Deity/etc.)):role]` |
> **Social Class** | `INPUT[list(placeholder(Commoner/Noble/etc.)):social_class]` |
> **Profession** | `INPUT[list(placeholder(Warrior/Merchant/etc.)):profession]` |
> **Organization** | `INPUT[inlineListSuggester(optionQuery(#organization AND !"Templates"), useLinks(partial)):organization]` |
> 
> #### World Connections
>  |
> ---|---|
> **Location** | `INPUT[inlineListSuggester(optionQuery(#settlement or #poi or #geography or #country or #cosmos AND !"Templates"), useLinks(partial)):location]` |
> **Hometown** | `INPUT[inlineListSuggester(optionQuery(#settlement or #geography AND !"Templates"), useLinks(partial)):hometown]` |
> **Follows Religion** | `INPUT[inlineListSuggester(optionQuery(#religion AND !"Templates"), useLinks(partial)):follows_religion]` |
> **Speaks** | `INPUT[inlineListSuggester(optionQuery(#language AND !"Templates"), useLinks(partial)):speaks]` |
> **Knows Magic** | `INPUT[inlineListSuggester(optionQuery(#magic AND !"Templates"), useLinks(partial)):knows_magic]` |
> **Owns** | `INPUT[inlineListSuggester(optionQuery(#object AND !"Templates"), useLinks(partial)):owns]` |
> **Conditions** | `INPUT[inlineListSuggester(optionQuery(#condition AND !"Templates"), useLinks(partial)):conditions]` |
> 
> #### Relationships
>  |
> ---|---|
> **Family** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):family]` |
> **Allies** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):allies]` |
> **Enemies** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):enemies]` |
> **Lover** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):lover]` |
> **Other Relations** | `INPUT[inlineListSuggester(optionQuery(#character AND !"Templates"), useLinks(partial)):other_relations]` |
> 
> #### History
>  |
> ---|---|
> **Involved In** | `INPUT[inlineListSuggester(optionQuery(#history AND !"Templates"), useLinks(partial)):involved_in]` |
> **Created** | `INPUT[inlineListSuggester(optionQuery(#object or #lore or #organization AND !"Templates"), useLinks(partial)):created]` |
> 
> #### Calendar & Timeline Integration
>  |
> ---|---|
> **Calendar** | `INPUT[text:fc-calendar]` |
> **Event Category** | `INPUT[text(placeholder(Birth/Death/Reign/etc.)):fc-category]` |
> **Display Name** | `INPUT[text(placeholder(Override character name)):fc-display-name]` |
> **Timeline Image** | `INPUT[text(placeholder([[character-portrait.jpg]] LINK!)):aat-event-picture]` |
> **Show in Timeline** | `INPUT[toggle:aat-render-enabled]` |
> **Timeline Body** | `INPUT[textArea(placeholder(Custom description for timeline)):aat-event-body]` |
> **Additional Timelines** | `INPUT[list(placeholder(character-timeline/family-history)):timelines]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Character.base|All Characters]] | [[Home]]
>
> [[#Overview]] • [[#Physical Description]] • [[#Personality]] • [[#Relationships]]
> 
> [[#History & Background|History]] • [[#Goals & Motivations|Goals]] • [[#Story Notes]]

# **`=this.file.name`**

> [!statbox]+
> # `=this.file.name`
> `VIEW[!\[\[{art}\]\]][text(renderMarkdown)]`
> 
> <div class="section">Basic Information</div>
> 
> <span class="label">Aliases</span> `VIEW[{aliases}]`
> 
> <span class="label">Ancestry</span> `VIEW[{ancestry}][link]`
> 
> <span class="label">Age</span> `VIEW[{age}]`
> 
> <span class="label">Gender</span> `VIEW[{gender}]`
> 
> <span class="label">Status</span> `VIEW[{life_status}]`
> 
> <div class="section">Current Details</div>
> 
> <span class="label">Location</span> `VIEW[{location}][link]`
> 
> <span class="label">Organization</span> `VIEW[{organization}][link]`
> 
> <span class="label">Role</span> `VIEW[{role}]`
> 
> <span class="label">Profession</span> `VIEW[{profession}]`

## Overview
Brief description of who this character is and their role in the world.

## Physical Description
How the character looks, distinguishing features, typical clothing or appearance.

## Personality
What makes this character unique - their mannerisms, values, fears, quirks, and defining traits.

## Relationships
Key relationships and how they shape this character. Family dynamics, friendships, rivalries, romantic connections.

## History & Background
Where they came from, formative experiences, major events they've been involved in, and things they've created or accomplished.

## Goals & Motivations
What drives this character - current pursuits, long-term aspirations, fears and concerns.

## Story Notes
Narrative details, character arc tracking, POV considerations, and story-specific development.

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Character Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Character folder
const targetFolder = "World/Character";
await tp.file.move(`${targetFolder}/${title}`);
_%>