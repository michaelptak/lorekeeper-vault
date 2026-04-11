---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Notes|All Notes]] | [[Home]]
# Documentation

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Note
> `BUTTON[NotesNoteSelector]`

```base
filters:
  and:
    - or:
        - note_purpose.contains("Documentation")
        - note_purpose.contains("Vault")
        - file.path.contains("Notes/Documentation")
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.mtime
      - note_purpose
      - status
    sort:
      - property: status
        direction: ASC
    columnSize:
      file.mtime: 221

```