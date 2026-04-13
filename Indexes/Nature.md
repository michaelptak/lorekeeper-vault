---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Home]]
# Nature
> [!lk-actions] New Nature
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
