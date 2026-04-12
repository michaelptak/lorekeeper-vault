---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Notes

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Excalidraw
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
