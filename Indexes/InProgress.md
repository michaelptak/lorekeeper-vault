---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Home]]
# In Progress
> [!lk-note] Note
> Notes where `status` = `WIP` 
```base
filters:
  and:
    - or:
        - status.contains("WIP")
    - '!file.path.contains("Templates")'
    - '!file.path.contains("Archive")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.tags
      - file.mtime
      - status
    sort:
      - property: note_purpose
        direction: ASC
    columnSize:
      file.mtime: 221

```