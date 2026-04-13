---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Home]]
# Notes

> [!lk-actions] New Excalidraw
> `BUTTON[New-Excalidraw]`

```base
filters:
  and:
    - file.tags.contains("Excalidraw")
    - '!file.path.contains("Templates")'
    - '!file.path.contains("Archive")'
    - '!file.path.contains("Notes/Documentation")'
views:
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
