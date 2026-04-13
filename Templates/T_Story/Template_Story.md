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
story_notes:
cssclasses:
  - lk-dashboard
  - hcl
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
> # <% title %>
> *A story takes shape*

> [!lk-highlight]
> [[Story|All Stories]] | [[Home]]

> [!lk-info]
>> [!lk-col] Actions
>> - `BUTTON[StoryNotesSelector]`
>> - `BUTTON[NewScene]`
>> - `BUTTON[CompileManuscript]`
>
>> [!lk-col] Quick Notes
>> `INPUT[textArea(placeholder(Jot down ideas...)):story_notes]`
>
>> [!lk-col] Progress
>> ```dataviewjs
>> const pages = dv.pages('#Scene').where(p => p.story_title === "<% title %>");
>> let totalWords = 0;
>> for (const page of pages) {
>>     const content = await dv.io.load(page.file.path);
>>     const body = content.replace(/^---[\s\S]*?---/, '');
>>     totalWords += body.trim().split(/\s+/).filter(w => w.length > 0).length;
>> }
>> dv.paragraph(totalWords.toLocaleString() + " words | " + pages.length + " scenes");
>> ```
>> ```dataview
>> TABLE WITHOUT ID
>> status + ": " + length(rows) as "Count"
>> FROM #Scene OR #Notes
>> WHERE story_title = "<% title %>"
>> GROUP BY status
>> SORT status
>> ```

## Scenes
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

## Related Notes
```base
filters:
  and:
    - story_title == "<% title %>"
    - '!file.hasTag("Scene")'
    - '!file.hasTag("Story")'
views:
  - type: table
    name: Notes
    order:
      - file.name
      - note_purpose
      - status
      - file.mtime
    sort:
      - property: note_purpose
        direction: ASC
    columnSize:
      note.note_purpose: 120
      note.status: 100

```
