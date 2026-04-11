---
tags: Notes
status:
related:
note_purpose: Brainstorm
story_title:
priority:
---
> [!metadata]- Meta Data
> #### General
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> 
> #### Notes Properties
>  |
> ---|---|
> **Note Purpose** | Brainstorm |
> **Story Title** | `INPUT[text:story_title]` |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Notes.base|All Notes]] | [[Home]]
# **`=this.file.name`**
<%*
const hasNewNoteTitle = tp.file.title.startsWith("NewNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
if (hasNewNoteTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Brainstorm Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
const targetFolder = "Notes";
await tp.file.move(`${targetFolder}/${title}`);
_%>

