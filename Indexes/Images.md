---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Home]]
# Images
```base
filters:
  and:
    - file.path.contains("Assets")
    - '!file.path.contains("Templates")'
    - '!file.path.contains("Archive")'
views:
  - type: cards
    name: View
    image: file.file
  - type: table
    name: Table
    order:
      - file.name
      - file.mtime
      - status
    sort:
      - property: note_purpose
        direction: ASC
    columnSize:
      file.name: 187
      file.mtime: 233

```
