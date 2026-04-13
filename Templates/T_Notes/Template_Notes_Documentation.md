---
tags: Notes
status:
related:
note_purpose: Documentation
story_title:
priority:
---
> [!lk-navbar]+ Navigation
> [[Documentation|Documentation]] | [[Notes|All Notes]] | [[Home]]
# **`=this.file.name`**
<%*
const hasNewNoteTitle = tp.file.title.startsWith("NewNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
if (hasNewNoteTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Documentation Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
const targetFolder = "Notes/Documentation";
await tp.file.move(`${targetFolder}/${title}`);
_%>