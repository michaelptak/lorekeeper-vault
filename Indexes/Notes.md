---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Documentation|Documentation]] | [[Home]]
# Notes

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Note
> `BUTTON[NotesNoteSelector]`

```base
filters:
  and:
    - file.tags.contains("Notes")
    - '!file.path.contains("Templates")'
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
