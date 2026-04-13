<%*
const selectedStory = window._lk_story || "";
if (window._lk_story) delete window._lk_story;

const hasNewNoteTitle = tp.file.title.startsWith("NewNote") || tp.file.title.startsWith("NewStoryNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewNoteTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Reference Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

await tp.file.move(`Notes/${title}`);
_%>
---
tags: Notes
status:
related:
note_purpose: Reference
story_title: <% selectedStory %>
priority:
---
> [!lk-navbar]+ Navigation
> <% selectedStory ? '[[' + selectedStory + ']] | ' : '' %>[[Notes|All Notes]] | [[Home]]
# **`=this.file.name`**
