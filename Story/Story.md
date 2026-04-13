---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Home]]

# Story Dashboard

> [!lk-actions] Add A Story
> `BUTTON[NewStory]`

```base
filters:
  and:
    - '!file.path.contains("Templates")'
    - '!file.path.contains("Archive")'
    - file.tags.contains("#Story")
views:
  - type: table
    name: Table
    order:
      - file.name
      - status
      - file.mtime
      - file.tags
    sort:
      - property: note_purpose
        direction: ASC
    columnSize:
      file.mtime: 221

```
