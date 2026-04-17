<%*
const hasNewStoryTitle = tp.file.title.startsWith("NewStoryNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

const abort = async (msg) => {
    new Notice(msg, 5000);
    const f = tp.config.target_file;
    setTimeout(() => app.vault.delete(f), 500);
};

if (hasNewStoryTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter story name");
    if (!title) { await abort("Story creation cancelled."); return; }
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
const targetFolder = `Story/${title}`;
await tp.file.move(`${targetFolder}/${title}`);

// Create Draft 1 folder
const draftFolder = `${targetFolder}/Draft 1`;
if (!app.vault.getFolderByPath(draftFolder)) {
    await app.vault.createFolder(draftFolder);
}
_%>
---
tags:
  - Story
art: Assets/TemplateImg/Placeholder-Generic.jpg
status:
related:
story_title: <% title %>
active_draft: true
draft: 1
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
> **Draft** | `VIEW[{draft}]` |
> **Active Draft** | `INPUT[toggle:active_draft]` |

> [!lk-hero]
> # <% title %>
> *A story takes shape*

> [!lk-highlight]
> [[Story|All Stories]] | [[Home]]

> [!lk-info]
>> [!lk-col] Actions
>> - `BUTTON[StoryNotesSelector]`
>> - `BUTTON[NewChapter]`
>> - `BUTTON[NewDraft]`
>> - `BUTTON[CompileManuscript]`
>
>> [!lk-col] Quick Notes
>> `INPUT[textArea(placeholder(Jot down ideas...)):story_notes]`
>
>> [!lk-col] Progress
>> ```dataviewjs
>> const storyTitle = "<% title %>";
>> const draftPath = "Story/" + storyTitle + "/Draft 1";
>> const pages = dv.pages('#Chapter').where(p => p.story_title === storyTitle && p.file.folder === draftPath);
>> let totalWords = 0;
>> for (const page of pages) {
>>     const content = await dv.io.load(page.file.path);
>>     const body = content.replace(/^---[\s\S]*?---/, '');
>>     totalWords += body.trim().split(/\s+/).filter(w => w.length > 0).length;
>> }
>> dv.paragraph(totalWords.toLocaleString() + " words | " + pages.length + " chapters (Draft 1)");
>> ```
>> ```dataview
>> TABLE WITHOUT ID
>> status + ": " + length(rows) as "Count"
>> FROM #Chapter OR #Notes
>> WHERE story_title = "<% title %>"
>>   AND (contains(file.tags, "#Notes") OR file.folder = "Story/<% title %>/Draft 1")
>> GROUP BY status
>> SORT status
>> ```

## Chapters
```base
filters:
  and:
    - file.hasTag("Chapter")
    - story_title == "<% title %>"
    - draft == 1
views:
  - type: table
    name: Chapters
    order:
      - file.name
      - chapter-number
      - status
      - pov
      - related
      - involves_world
      - chapter_outline
    sort:
      - property: chapter-number
        direction: ASC

```

## Related Notes
```base
filters:
  and:
    - story_title == "<% title %>"
    - '!file.hasTag("Chapter")'
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
      note.note_purpose: 159
      note.status: 100

```

## Drafts
```base
filters:
  and:
    - file.hasTag("Story")
    - story_title == "<% title %>"
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Drafts
    order:
      - file.name
      - draft
      - active_draft
      - status
    sort:
      - property: draft
        direction: ASC
```
