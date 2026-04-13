---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Home]]
# Magic

> [!lk-actions] New Magic Entry
> `BUTTON[NewMagic]`

```base
filters:
  and:
    - file.tags.contains("Magic")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
      - practiced_by
      - file.mtime
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
