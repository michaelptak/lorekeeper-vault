---
tags: Meta
status:
related:
purpose: Research
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
> **Purpose** | Research |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |
> **Project ID** | `INPUT[text:project_id]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Research.base|Research]] | [[Meta.base|All Meta Notes]] | [[Home]]
# **`=this.file.name`**
<!-- 
FIELD GUIDANCE (delete after filling out):
- tags: Choose relevant tag if researching that particular topic
- related: Choose any directly related notes.
-->

<%*
const hasNewMetaTitle = tp.file.title.startsWith("NewMetaNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;
if (hasNewMetaTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Research Note Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}
const targetFolder = "Meta/Research";
await tp.file.move(`${targetFolder}/${title}`);
_%>