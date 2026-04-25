---
cssclasses:
  - lk-dashboard
  - hcl
---

> [!lk-hero]
> # Your World Name

> [!lk-actions]
> `BUTTON[WorldNoteSelector]` `BUTTON[NotesNoteSelector]`  `BUTTON[StoryNoteSelector]`  `BUTTON[StoryNotesSelector]` 
> `BUTTON[New-Excalidraw]`  `BUTTON[OpenWebViewer]`

> [!lk-cards|2]
> ![[card-story.jpeg]]
> **[[Story]]**
>
> ![[card-notes.jpeg]]
> **[[Notes]]**

> [!lk-cards|2]
> ![[card-inprogress.jpeg]]
> **[[InProgress|In Progress]]**
>
> ![[card-map.jpeg]]
> **[[ExampleMap|Map]]**

## World

> [!lk-cards|4]
> ![[card-characters.jpeg]]
> **[[Character]]**
>
> ![[card-ancestry.jpeg]]
> **[[Ancestry]]**
>
> ![[card-organization.jpeg]]
> **[[Organization]]**
>
> ![[card-art.jpeg]]
> **[[Art]]**
>
> ![[card-settlement.jpeg]]
> **[[Settlement]]**
>
> ![[card-geography.jpeg]]
> **[[Geography]]**
>
> ![[card-poi.jpeg]]
> **[[POI|POI]]**
>
> ![[card-history.jpeg]]
> **[[History]]**
>
> ![[card-country.jpeg]]
> **[[Country]]**
>
> ![[card-lore.jpeg]]
> **[[Lore]]**
>
> ![[card-religion.jpeg]]
> **[[Religion]]**
>
> ![[card-concept.jpeg]]
> **[[Concept]]**
>
> ![[card-magic.jpeg]]
> **[[Magic]]**
>
> ![[card-object.jpeg]]
> **[[Object]]**
>
> ![[card-nature.jpeg]]
> **[[Nature]]**
>
> ![[card-technology.jpeg]]
> **[[Technology]]**
>
> ![[card-language.jpeg]]
> **[[Language]]**
>
> ![[card-misc.jpeg]]
> **[[Misc]]**

## Recent

```base
filters:
  and:
    - '!file.inFolder("Templates")'
    - '!file.inFolder("Archive")'
    - '!file.inFolder(".obsidian")'
    - file.ext == "md"
views:
  - type: table
    name: Recent Files
    order:
      - file.name
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
    limit: 10
```

## Resources

> [!lk-links]
> - [[Documentation]]
> - [[Master Tags List]]
> - [[Quality Control Dashboard]]
> - [[Buttons]]
> - [[Notes|All Notes]]
> - [[Scratch Note]]
> - [[Excalidraw|All Excalidraw Notes]]
> - [[Images|All Images]]
