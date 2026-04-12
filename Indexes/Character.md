---
cssclasses:
  - hcl
obsidianUIMode: preview
---
> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> [[Home]]
# Characters

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] New Character
> `BUTTON[NewCharacter]`

```base
filters:
  and:
    - file.tags.contains("Character")
    - file.path.startsWith("World/")
views:
  - type: table
    name: View
    order:
      - file.name
      - tags
      - status
      - role
      - life_status
      - aliases
      - age
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
    image: note.art
    columnSize:
      note.aliases: 145
  - type: cards
    name: Cards
    sort:
      - property: file.mtime
        direction: DESC
    image: note.art

```
