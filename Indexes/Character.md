---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Characters

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Character
> `BUTTON[WorldNoteSelector]`

```base
filters:
  and:
    - file.tags.contains("Character")
    - '!file.path.contains("Templates/")'
views:
  - type: table
    name: View
    sort:
      - property: file.mtime
        direction: DESC
    image: note.art
  - type: cards
    name: Cards
    sort:
      - property: file.mtime
        direction: DESC
    image: note.art
```
