---
cssclasses:
  - hcl
---
# Story Dashboard

> [!tip|c-plain no-i text-center title-center wsmall callout-bordered center] Add A Story
> `BUTTON[NewStory]`

> [!base|no-i no-t]
> ```base
> filters:
>   and:
>     - file.hasTag("Story")
> views:
>   - type: table
>     name: All Stories
>     order:
>       - file.name
>       - status
>       - file.mtime
> ```
---