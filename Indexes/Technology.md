---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Technology

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Technology
> `BUTTON[NewTechnology]`

```base
filters:
  and:
    - file.tags.contains("Technology")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
      - created_by
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
