<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewStoryTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter story name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
// Move file to Plot folder
const targetFolder = `Story/${title}`;
await tp.file.move(`${targetFolder}/${title}`);
_%>
---
tags:
  - Story
art: Assets/TemplateImg/Placeholder-Generic.jpg
status:
related:
story_title: <% title %>
cssclasses: dvl-c
obsidianUIMode: preview
---

> [!metadata]- Story Data
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

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Story|All Stories]] | [[Home]]
# **<% title %>**

> [!column|flex 3 no-i no-t]
>> [!tip|no-i] Quick Add Buttons
>> - 📝 `BUTTON[NewPlot]`
>> - 🎬 `BUTTON[NewScene]`
>> - `BUTTON[CompileManuscript]`
>
>> [!warning|no-i] Notes
>>  `INPUT[textArea(placeholder(Add any quick notes here. Works in view mode!)):story_notes]`
>
>> [!success|no-i] Progress
>> ```dataview
>> TABLE WITHOUT ID
>> status + ": " + length(rows) as "Count"
>> FROM #Plot OR #Scene
>> WHERE story_title = "<% title %>"
>> GROUP BY status
>> SORT status
>> ```

## Plot Overview
```base
filters:
  and:
    - file.hasTag("Plot")
    - story_title == "<% title %>"
views:
  - type: table
    name: Plots
    order:
      - file.name
      - status
      - file.mtime
      - plot_type
      - plot_focus
      - plot_scope
      - related
      - involves_world
    sort: []
    columnSize:
      note.status: 141
      file.mtime: 225
      note.plot_type: 102
      note.plot_focus: 162

```

## Scene Overview
```base
filters:
  and:
    - file.hasTag("Scene")
    - story_title == "<% title %>"
views:
  - type: table
    name: Scenes
    order:
      - file.name
      - story_order
      - status
      - revisions
      - pov
      - related
      - involves_world
    sort:
      - property: story_order
        direction: ASC
    columnSize:
      note.status: 84
      note.revisions: 97

```

## Other Related Notes
```base
filters:
  or:
    - related.contains("<% title %>")
    - project_id == "<% title %>"
views:
  - type: table
    name: Scenes
    order:
      - file.name
      - status
    sort:
      - property: story_order
        direction: ASC

```
