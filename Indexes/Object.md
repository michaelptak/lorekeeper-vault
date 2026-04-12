---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Objects

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Object
> `BUTTON[NewObject]`

```base
filters:
  and:
    - file.tags.contains("Object")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
      - rarity
      - file.mtime
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
