<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
let selectedStory;

if (hasNewStoryTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Scene Name");
    
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

// Move file to Scene folder
const targetFolder = "Story/Scene";
await tp.file.move(`${targetFolder}/${title}`);
_%>
---
tags:
  - Scene
art: Assets/TemplateImg/Placeholder-Generic.jpg
story_title: <% selectedStory %>
status:
related:
story_order:
fc-date:
fc-end:
involves_world:
pov_character:
fc-calendar: 
fc-category:
fc-display-name:
aat-event-picture:
aat-render-enabled: true
aat-event-body:
timelines: []
---

> [!metadata]- Scene Data
> #### Core Properties
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> **Art** | `INPUT[imageSuggester(optionQuery("Assets/WorldImg")):art]` |
> 
> #### Story Details
>  |
> ---|---|
> **Story Title** | `INPUT[text(placeholder(The Fellowship of the Ring)):story_title]` |
> **Story Order** | `INPUT[text(placeholder(1.2.3 [ch.scene.beat])):story_order]` |
> **Start Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-date]` |
> **End Date** | `INPUT[text(placeholder(YYYY-MM-DD)):fc-end]` |
> **POV Character** | `INPUT[inlineListSuggester(optionQuery(#Character AND !"Templates"), useLinks(partial)):pov_character]` |
> 
> #### World Connections
>  |
> ---|---|
> **Involves World Elements** | `INPUT[inlineListSuggester(optionQuery("World"), useLinks(partial)):involves_world]` |
> 
> #### Timeline Integration
>  |
> ---|---|
> **Calendar** | `INPUT[text:fc-calendar]` |
> **Event Category** | `INPUT[text:fc-category]` |
> **Display Name** | `INPUT[text(placeholder(Override scene title)):fc-display-name]` |
> **Timeline Image** | `INPUT[text(placeholder([[scene-image.jpg]] LINK!)):aat-event-picture]` |
> **Show in Timeline** | `INPUT[toggle:aat-render-enabled]` |
> **Timeline Body** | `INPUT[textArea(placeholder(Custom description for timeline)):aat-event-body]` |
> **Additional Timelines** | `INPUT[list(placeholder(story-timeline/chapter-timeline)):timelines]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[<% selectedStory %>]] | [[Story|All Stories]] | [[Home]]

# **`=this.file.name`**