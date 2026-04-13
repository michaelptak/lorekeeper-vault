---
tags:
  - Story
art: Assets/TemplateImg/Placeholder-Generic.jpg
status:
related:
story_title: Test
story_notes:
cssclasses:
  - lk-dashboard
obsidianUIMode: preview
---

> [!lk-metadata]- Story Data
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

> [!lk-hero]
> # Test
> *A story takes shape*

> [!lk-highlight]
> [[Story|All Stories]] | [[Home]]

> [!lk-info]
>> [!lk-col] Actions
>> - `BUTTON[NewPlot]`
>> - `BUTTON[NewScene]`
>> - `BUTTON[CompileManuscript]`
>
>> [!lk-col] Quick Notes
>> `INPUT[textArea(placeholder(Jot down ideas, reminders, things to fix...)):story_notes]`
>
>> [!lk-col] Progress
>> ```dataview
>> TABLE WITHOUT ID
>> status + ": " + length(rows) as "Count"
>> FROM #Plot OR #Scene
>> WHERE story_title = "Test"
>> GROUP BY status
>> SORT status
>> ```

## Plot Overview
```base
filters:
  and:
    - file.hasTag("Plot")
    - story_title == "Test"
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
    - story_title == "Test"
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
    - related.contains("Test")
    - project_id == "Test"
views:
  - type: table
    name: Related
    order:
      - file.name
      - status
    sort:
      - property: story_order
        direction: ASC

```
