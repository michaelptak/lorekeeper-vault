---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Magic

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Magic Entry
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
