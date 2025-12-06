---
tags: Meta
status: Archived
related:
purpose: Daily-Note
priority:
project_id:
---
> [!metadata]- Meta Data
> #### General
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> 
> #### Meta Properties
>  |
> ---|---|
> **Purpose** | Daily-Note |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |
> **Project ID** | `INPUT[text:project_id]` |
# **`=this.file.name`**
## Notes
>[!info] Old Template
>This note is currently defunct as I feel daily notes have been superseded by other categories. Nonetheless, it is here for safe keeping.

## WIP Notes
![[In-Progress-Notes.base]]

## Quick Links
[[Scratch Note]]

<%*
const hasNewMetaTitle = tp.file.title.startsWith("NewMetaNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewMetaTitle || hasUntitledTitle) {
    const currentDate = tp.date.now("YYYY-MM-DD");
    const userTitle = await tp.system.prompt("Enter Daily Note Name (date will be added automatically)");
    title = `${currentDate} - ${userTitle}`;
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

const targetFolder = "Meta/Daily-Note";
await tp.file.move(`${targetFolder}/${title}`);
_%>