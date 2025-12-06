---
tags:
  - Meta
status:
related:
purpose:
  - Reference
  - Image Board
priority:
project_id:
"":
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
> **Purpose** | Reference |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |
> **Project ID** | `INPUT[text:project_id]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Reference.base|Reference]] | [[Meta.base|All Meta Notes]] | [[Home]]
# **`=this.file.name`**
`CTRL+ALT+E` once created to toggle between note mode
`BUTTON[Convert-Excalidraw]`

`INPUT[imageListSuggester(optionQuery("Assets/Reference")):art]`
<%*
const hasNewMetaTitle = tp.file.title.startsWith("NewMetaNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
if (hasNewMetaTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Reference Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
const targetFolder = "Meta/Reference";
await tp.file.move(`${targetFolder}/${title}`);
_%>