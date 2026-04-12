---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Languages

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Language
> `BUTTON[WorldNoteSelector]`

```base
filters:
  and:
    - file.tags.contains("Language")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
      - spoken_by
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
