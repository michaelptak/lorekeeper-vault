<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
let selectedStory;

if (hasNewStoryTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Plot Element Name");
    
    // Get all existing Story notes
    const storyFiles = app.vault.getFiles()
        .filter(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache?.frontmatter?.tags?.includes("Story") && cache?.frontmatter?.story_title;
        });
    
    if (storyFiles.length > 0) {
        // Create arrays for suggester
        const storyTitles = storyFiles.map(file => {
            const cache = app.metadataCache.getFileCache(file);
            return cache.frontmatter.story_title;
        });
        
        // Let user select from existing stories
        selectedStory = await tp.system.suggester(storyTitles, storyTitles);
        
        if (!selectedStory) {
            // User cancelled selection
            return;
        }
    } else {
        // No existing stories found
        selectedStory = await tp.system.prompt("No existing stories found. Enter story title:");
    }
    
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Plot folder
const targetFolder = `Story/${selectedStory}/Plot`;
await tp.file.move(`${targetFolder}/${title}`);
_%>
---
tags:
  - Plot
art: Assets/TemplateImg/Placeholder-Generic.jpg
story_title: <% selectedStory %>
status:
related:
plot_type:
plot_scope:
plot_focus:
story_order:
scenes:
pov_character:
involves_world:
---

> [!lk-metadata]- Plot Data
> #### Core Properties
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> **Art** | `INPUT[imageSuggester(optionQuery("Assets/WorldImg")):art]` |
> 
> #### Story Structure
>  |
> ---|---|
> **Story Title** | `INPUT[text(placeholder(The Fellowship of the Ring)):story_title]` |
> **Plot Type** | `INPUT[text(placeholder(Arc/Conflict/Theme/Outline/Beat)):plot_type]` |
> **Plot Scope** | `INPUT[text(placeholder(Story/Act/Chapter)):plot_scope]` |
> **Plot Focus** | `INPUT[text(placeholder(Character Arc/World Conflict/Thematic Element)):plot_focus]` |
> **Story Order** | `INPUT[text(placeholder(1.1 = Chapter 1 - Scene 1)):story_order]` |
> 
> #### Scene Planning
>  |
> ---|---|
> **Linked Scenes** | `INPUT[inlineListSuggester(optionQuery(#Scene AND !"Templates"), useLinks(partial)):scenes]` |
> **POV Character** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates"), useLinks(partial)):pov_character]` |
> 
> #### World Connections
>  |
> ---|---|
> **Involves World Elements** | `INPUT[inlineListSuggester(optionQuery("World"), useLinks(partial)):involves_world]` |

> [!lk-navbar]+ Navigation
> [[<% selectedStory %>]] | [[Story|All Stories]] | [[Home]]

# **`=this.file.name`**

## Overview
<!-- What is this plot element about? Summary, purpose, themes -->

## Key Beats
<!-- Major story beats, turning points, conflicts -->

## Character Arcs
<!-- How do characters change through this section? -->

## World Elements
<!-- Important worldbuilding aspects, settings, magic systems at play -->

## Notes
<!-- Additional planning thoughts, alternatives considered, etc. -->