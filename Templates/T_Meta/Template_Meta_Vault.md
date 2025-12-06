---
tags: Meta
status:
related:
purpose: Vault
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
> **Purpose** | Vault |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |
> **Project ID** | `INPUT[text:project_id]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Obsidian-Vault.base|Vault Notes]] | [[Meta.base|All Meta Notes]] | [[Home]]
# **`=this.file.name`**
<%*
const hasNewMetaTitle = tp.file.title.startsWith("NewMetaNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
if (hasNewMetaTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Vault Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
const targetFolder = "Meta/Vault";
await tp.file.move(`${targetFolder}/${title}`);
_%>