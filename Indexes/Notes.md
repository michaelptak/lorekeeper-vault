---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!lk-navbar]+ Navigation
> [[Documentation|Documentation]] | [[Home]]
# Notes

> [!lk-actions] New Note
> `BUTTON[NotesNoteSelector]`

```base
filters:
  and:
    - file.tags.contains("Notes")
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
      - note_purpose
      - story_title
      - priority
      - related
    columnSize:
      file.mtime: 233

```
