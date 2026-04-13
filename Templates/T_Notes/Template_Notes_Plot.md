<%*
const selectedStory = window._lk_story || "";
if (window._lk_story) delete window._lk_story;

const hasNewNoteTitle = tp.file.title.startsWith("NewNote") || tp.file.title.startsWith("NewStoryNote");
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewNoteTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Plot Note Name");
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
note_purpose: Plot
story_title: <% selectedStory %>
priority:
---
> [!lk-navbar]+ Navigation
> <% selectedStory ? '[[' + selectedStory + ']] | ' : '' %>[[Notes|All Notes]] | [[Home]]
# **`=this.file.name`**

## Overview
<!-- What is this plot element about? Summary, purpose, themes -->

## Key Beats
<!-- Major story beats, turning points, conflicts -->

## Character Arcs
<!-- How do characters change through this section? -->

## World Elements
<!-- Important worldbuilding aspects, settings, magic systems at play -->

## Notes
<!-- Additional planning thoughts, alternatives considered, etc. -->
