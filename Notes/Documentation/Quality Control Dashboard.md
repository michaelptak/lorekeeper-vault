---
tags: Notes
status: Complete
related:
note_purpose: Vault
story_title:
priority: High
---

> [!lk-navbar]+ Navigation
> **Quick Links:** [[Documentation|Documentation]] | [[Notes|All Notes]] | [[Home]]
# **Quality Control Dashboard**

This dashboard helps maintain vault quality by identifying notes that need attention.
**Not Everything here is/will be an issue**.
However it has some useful trackers for notes that you may want to have a look at.

---

## Stub Notes (Need Content)

```base
filters:
  and:
    - status.contains("Stub")
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.folder
      - status
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
```

---

## Work In Progress Notes

```base
filters:
  and:
    - status.contains("WIP")
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.folder
      - priority
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
```

---

## Planned Notes (Not Started)

```base
filters:
  and:
    - status.contains("Planned")
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.folder
      - priority
      - file.ctime
    sort:
      - property: file.ctime
        direction: DESC

```

---

## Recently Completed Notes

```base
filters:
  and:
    - status.contains("Complete")
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.folder
      - file.mtime
    sort:
      - property: file.mtime
        direction: ASC
    limit: 10

```

---

## Notes with Placeholder Art
Notes that still have the default template image in their `art` property.

```base
filters:
  and:
    - art.contains("Assets/TemplateImg/")
    - '!file.path.contains("Templates")'
    - '!file.path.contains("Archive")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.folder
      - status
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
```

---

## High Priority Incomplete Notes

```base
filters:
  and:
    - or:
        - status.contains("WIP")
        - status.contains("Stub")
        - status.contains("Planned")
    - priority.contains("High")
    - '!file.path.contains("Templates")'
views:
  - type: table
    name: Table
    order:
      - file.name
      - file.folder
      - status
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
```
