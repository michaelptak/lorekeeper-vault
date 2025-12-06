---
tags:
  - Timeline
---

> [!metadata]- Meta Data
> #### Core Properties
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> 
> #### Timeline Filters (Optional)
>  |
> ---|---|
> **Historical Scope** | `INPUT[HistoricalScope][:historical_scope]` |
> **Scope** | `INPUT[Scope][:scope]` |
> **Era** | `INPUT[text(placeholder(The Great Convergence)):era]` |
> **Timeline Name** | `INPUT[text:timelines]` |

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Timeline.base|All Timelines]] | [[Home]]
# **`=this.file.name`**
>[!note]
>Add timeline(s) to code block below

```aat-vertical

```

<%*
const hasNewWorldTitle = tp.file.title.startsWith("NewWorldNote"); 
const hasUntitledTitle = tp.file.title.startsWith("Untitled");
let title;

if (hasNewWorldTitle || hasUntitledTitle) {
    title = await tp.system.prompt("Enter Timeline Name");
    await tp.file.rename(title);
} else {
    title = tp.file.title;
}

// Move file to History folder
const targetFolder = "World/Timeline";
await tp.file.move(`${targetFolder}/${title}`);
_%>