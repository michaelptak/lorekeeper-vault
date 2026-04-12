---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Concepts

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Concept
> `BUTTON[WorldNoteSelector]`

```base
filters:
  and:
    - file.tags.contains("Concept")
    - '!file.path.contains("Templates/")'
    - '!file.path.contains("Archive/")'
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
    sort:
      - property: file.mtime
        direction: DESC
    image: note.art
    columnSize:
      note.tags: 160
  - type: cards
    name: Cards
    sort:
      - property: file.mtime
        direction: DESC
    image: note.art

```
