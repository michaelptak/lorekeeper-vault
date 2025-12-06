---
tags: Meta
status: Complete
related:
purpose: Planning
priority: Med
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

# **`=this.file.name`**
- [ ] To-Do