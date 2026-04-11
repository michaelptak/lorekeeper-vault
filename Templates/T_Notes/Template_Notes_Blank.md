---
tags: Notes
status:
related:
note_purpose:
story_title:
priority:
---

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Notes.base|All Notes]] | [[Home]]
# **`=this.file.name`**

<%*
const hasNewNoteTitle = tp.file.title.startsWith("NewNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewNoteTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Notes folder
const targetFolder = "Notes";
await tp.file.move(`${targetFolder}/${title}`);
_%>
