---
cssclasses:
  - lk-dashboard
  - hcl
---

> [!lk-hero]
> # Your World Name
> *Chronicle your creation*

> [!lk-actions]
> `BUTTON[WorldNoteSelector]` `BUTTON[StoryNoteSelector]` `BUTTON[NotesNoteSelector]` 
> `BUTTON[New-Excalidraw]`  `BUTTON[OpenWebViewer]`

> [!lk-cards|2]
> ![[quill-and-ink.jpeg]]
> **[[Story]]**
>
> ![[card-flora.jpeg]]
> **[[Notes]]**

> [!lk-cards|2]
> ![[medieval-forge.jpg]]
> **[[InProgress|In Progress]]**
>
> ![[example-map.jpg]]
> **[[ExampleMap|Map]]**

## World

> [!lk-cards|4]
> ![[card-characters.jpg]]
> **[[Character|Character]]**
>
> ![[card-ancestry.jpg]]
> **[[Ancestry|Ancestry]]**
>
> ![[card-organization.jpg]]
> **[[Organization|Organization]]**
>
> ![[card-art.jpeg]]
> **[[Art|Art]]**
>
> ![[card-settlement.jpeg]]
> **[[Settlement|Settlement]]**
>
> ![[card-geography.jpg]]
> **[[Geography]]**
>
> ![[card-poi.jpg]]
> **[[POI|POI]]**
>
> ![[card-history.jpg]]
> **[[History|History]]**
>
> ![[card-country.jpeg]]
> **[[Country]]**
>
> ![[card-lore.jpg]]
> **[[Lore|Lore]]**
>
> ![[card-religion.jpeg]]
> **[[Religion|Religion]]**
>
> ![[card-concept.jpg]]
> **[[Concept]]**
>
> ![[card-magic.jpeg]]
> **[[Magic|Magic]]**
>
> ![[card-object.jpg]]
> **[[Object]]**
>
> ![[card-creature.jpeg]]
> **[[Nature]]**
>
> ![[card-technology.jpg]]
> **[[Technology|Technology]]**
>
> ![[card-language.jpeg]]
> **[[Language|Language]]**
>
> ![[card-condition.jpg]]
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
