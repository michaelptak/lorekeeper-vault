---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Nature
> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Nature
> `BUTTON[NewNature]`

```base
filters:
  and:
    - file.tags.contains("Nature")
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
      - property: rarity
        direction: DESC
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
