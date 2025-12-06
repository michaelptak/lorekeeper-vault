---
tags: Meta
status:
related:
purpose:
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
> **Purpose** | `INPUT[select(option(Project), option(Planning), option(Research), option(Brainstorm), option(Daily-Note), option(Vault), option(Reference), option(Inspiration)):purpose]` |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |
> **Project ID** | `INPUT[text:project_id]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Meta.base|All Meta Notes]] | [[Home]]
# **`=this.file.name`**

<%*
const hasNewMetaTitle = tp.file.title.startsWith("NewMetaNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewMetaTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Meta Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to Meta folder
const targetFolder = "Meta";
await tp.file.move(`${targetFolder}/${title}`);
_%>
