---
obsidianUIMode: preview
cssclasses:
  - hcl
---
> [!lk-navbar]+ Navigation
> [[Home]]
# Ancestry

> [!lk-actions] New Ancestry
> `BUTTON[NewAncestry]`

```base
filters:
  and:
    - file.tags.contains("Ancestry")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
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
