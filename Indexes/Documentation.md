---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Notes|All Notes]] | [[Home]]
# Documentation

> [!lk-actions] New Note
> `BUTTON[NotesNoteSelector]`

```base
filters:
  and:
    - or:
        - note_purpose.contains("Documentation")
        - note_purpose.contains("Vault")
        - file.path.contains("Notes/Documentation")
    - '!file.path.contains("Templates")'
    - '!file.path.contains("Archive")'
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