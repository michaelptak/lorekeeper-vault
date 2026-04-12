---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# In Progress
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