---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# History

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New History Entry
> `BUTTON[WorldNoteSelector]`

```base
filters:
  and:
    - file.tags.contains("History")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
      - historical_scope
      - involved_countries
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
