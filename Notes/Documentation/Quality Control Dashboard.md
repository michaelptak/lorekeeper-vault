---
tags: Notes
status: Complete
related:
note_purpose: Vault
story_title:
priority: High
---

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c]+ Navigation
> **Quick Links:** [[Documentation.base|Documentation]] | [[Notes.base|All Notes]] | [[Home]]
# **Quality Control Dashboard**

This dashboard helps maintain vault quality by identifying notes that need attention.
**Not Everything here is/will be an issue**. 
However it has some useful trackers for notes that you may want to have a look at.

---

## 📊 Vault Overview

> [!summary]- Quick Stats
> ```dataview
> TABLE WITHOUT ID
>   "**Total Notes**" as "Metric",
>   length(rows) as "Count"
> FROM ""
> WHERE file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND file.ext = "md"
> GROUP BY true
> ```


---

## 🔍 Orphaned Notes Detection

Notes with **no incoming or outgoing links** (isolated from the vault knowledge graph).

> [!warning]- Orphaned Notes
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   file.mtime as "Modified"
> FROM ""
> WHERE file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND !contains(file.path, "Archive")
>   AND file.ext = "md"
>   AND length(file.outlinks) = 0
>   AND length(file.inlinks) = 0
> SORT file.mtime DESC
> ```

> [!info]- Notes With No Outgoing Links Only
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   length(file.inlinks) as "Incoming Links"
> FROM ""
> WHERE file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND !contains(file.path, "Archive")
>   AND file.ext = "md"
>   AND length(file.outlinks) = 0
>   AND length(file.inlinks) > 0
> SORT file.mtime DESC
> ```

---

## ⚠️ Incomplete Notes (Status Tracking)

Notes with incomplete or work-in-progress status that need attention.

> [!error]- Stub Notes (Need Content)
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   status as "Status",
>   file.mtime as "Modified"
> FROM ""
> WHERE status = "Stub"
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
> SORT file.mtime DESC
> ```

> [!warning]- Work In Progress Notes
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   priority as "Priority",
>   file.mtime as "Modified"
> FROM ""
> WHERE status = "WIP"
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
> SORT priority ASC, file.mtime DESC
> ```

> [!todo]- Planned Notes (Not Started)
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   priority as "Priority",
>   file.ctime as "Created"
> FROM ""
> WHERE status = "Planned"
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
> SORT priority ASC, file.ctime DESC
> ```

> [!question]- Notes Missing Status Field
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   file.mtime as "Modified"
> FROM ""
> WHERE !status
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND !contains(file.path, "Archive")
>   AND file.ext = "md"
> SORT file.mtime DESC
> LIMIT 50
> ```

---

## 🔗 Cross-Reference Validation

Identify broken links and missing references.

> [!failure]- Broken Links (Links to Non-Existent Notes)
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   file.outlinks as "Outgoing Links"
> FROM ""
> WHERE file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND file.ext = "md"
>   AND any(filter(file.outlinks, (x) => !x.file))
> SORT file.name ASC
> ```

> [!info]- Notes With Unlinked Mentions
> Notes that mention other note names but don't have proper wiki-links.
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   length(file.outlinks) as "Links"
> FROM ""
> WHERE file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND file.ext = "md"
>   AND length(file.outlinks) < 3
>   AND file.size > 1000
> SORT file.name ASC
> LIMIT 30
> ```

---

## 📝 Content Quality Checks

> [!hint]- Very Short Notes (Possible Stubs)
> Notes under 500 characters that might need expansion.
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   file.size as "Size (bytes)",
>   status as "Status"
> FROM ""
> WHERE file.size < 500
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND !contains(file.path, "Archive")
>   AND file.ext = "md"
> SORT file.size ASC
> LIMIT 30
> ```

> [!success]- Recently Completed Notes
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   file.mtime as "Completed"
> FROM ""
> WHERE status = "Complete"
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
> SORT file.mtime DESC
> LIMIT 20
> ```

---

## 🎨 Notes Without Art

Notes that have placeholders in their `art` property. Notes that simply do not have the property are not included. 

> [!note]- Notes with Placeholder Art
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   status as "Status",
>   file.mtime as "Modified"
> FROM ""
> WHERE contains(art, "Assets/TemplateImg/")
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
>   AND !contains(file.path, ".obsidian")
>   AND !contains(file.path, "Archive")
>   AND !contains(file.path, "Meta")
>   AND file.ext = "md"
> SORT file.mtime DESC
> ```

---

## 🎯 Action Items

> [!check]- High Priority Incomplete Notes
> ```dataview
> TABLE WITHOUT ID
>   file.link as "Note",
>   file.folder as "Folder",
>   status as "Status",
>   file.mtime as "Modified"
> FROM ""
> WHERE (status = "WIP" OR status = "Stub" OR status = "Planned")
>   AND priority = "High"
>   AND file.name != "Quality Control Dashboard"
>   AND !contains(file.path, "Templates")
> SORT file.mtime DESC
> ```

---

*Last updated: `= date(now)`*
