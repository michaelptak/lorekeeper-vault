---
tags: Notes
status: Complete
related:
note_purpose: Planning
story_title:
priority: Med
---

> [!metadata]- Meta Data
> #### General
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> 
> #### Notes Properties
>  |
> ---|---|
> **Note Purpose** | `INPUT[text:note_purpose]` |
> **Story Title** | `INPUT[text:story_title]` |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |

# **`=this.file.name`**
- [ ] To-Do