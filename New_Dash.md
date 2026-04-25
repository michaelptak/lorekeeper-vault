---
cssclasses:
  - lk-dashboard
  - hcl
world_name: Your World Name
---
```dataviewjs
// ── CONFIG ─────────────────────────────────────────────────
const TITLE        = dv.current().world_name || "Your World Name";
const STORY_FOLDER = "Story";
const WORLD_FOLDER = "World";
const EXCLUDE      = ["Templates", "Archive", ".obsidian"];
const KTR_PATH     = ".obsidian/plugins/keep-the-rhythm/data.json";
// ───────────────────────────────────────────────────────────

function excluded(p) { return EXCLUDE.some(x => p.startsWith(x)); }

const scenes = dv.pages(`"${STORY_FOLDER}"`).where(p => !excluded(p.file.path));
const world  = dv.pages(`"${WORLD_FOLDER}"`).where(p => !excluded(p.file.path));

let totalWords = 0, streak = 0;
try {
    const raw  = await app.vault.adapter.read(KTR_PATH);
    const data = JSON.parse(raw);
    const activity = data.stats?.dailyActivity || [];
    for (const entry of activity) {
        for (const ch of entry.changes || []) {
            if (ch.w > 0) totalWords += ch.w;
        }
    }
    streak = data.stats?.currentStreak || 0;
} catch (e) { /* KTR absent or different shape — zeros are fine */ }

// ── HERO ───────────────────────────────────────────────────
const hero = dv.el("div", "", { cls: "lk-hero-block" });
const left = hero.createDiv({ cls: "lk-hero-left" });

const dateStr = new Date().toLocaleDateString('en-US', { weekday: 'long', month: 'long', day: 'numeric', year: 'numeric' });

left.createDiv({ cls: "lk-hero-title", text: TITLE });
left.createDiv({ cls: "lk-hero-subtitle", text: `${dateStr}` });

const stats = hero.createDiv({ cls: "lk-hero-stats" });
[
    { val: totalWords > 0 ? totalWords.toLocaleString() : "—", label: "Words" },
    { val: scenes.length || "—", label: "Scenes" },
    { val: world.length  || "—", label: "World" },
    { val: streak > 0 ? `${streak}d` : "—", label: "Streak" },
].forEach(s => {
    const pill = stats.createDiv({ cls: "lk-hero-pill" });
    pill.createDiv({ cls: "lk-hero-val", text: String(s.val) });
    pill.createDiv({ cls: "lk-hero-label", text: s.label });
});
```

> [!lk-actions]
> `BUTTON[WorldNoteSelector]` `BUTTON[NotesNoteSelector]` `BUTTON[StoryNoteSelector]` `BUTTON[StoryNotesSelector]`
> `BUTTON[New-Excalidraw]` `BUTTON[OpenWebViewer]`

```dataviewjs
// ── CONFIG ─────────────────────────────────────────────────
const STORY_FOLDER = "Story";
const EXCLUDE      = ["Templates", "Archive", ".obsidian"];
// ───────────────────────────────────────────────────────────

const last = dv.pages(`"${STORY_FOLDER}"`)
    .where(p => !EXCLUDE.some(x => p.file.path.startsWith(x)))
    .sort(p => p.file.mtime, "desc")
    .first()
    ?? dv.pages()
        .where(p => !EXCLUDE.some(x => p.file.path.startsWith(x)))
        .sort(p => p.file.mtime, "desc")
        .first();

if (last) {
    const ms   = Date.now() - last.file.mtime.ts;
    const hrs  = Math.floor(ms / 3.6e6);
    const mins = Math.floor((ms % 3.6e6) / 6e4);
    const when = hrs >= 24 ? `${Math.floor(hrs / 24)}d ago`
               : hrs >= 1  ? `${hrs}h ago`
               : `${mins}m ago`;

    const card = dv.el("div", "", { cls: "lk-resume-card" });
    const info = card.createDiv({ cls: "lk-resume-info" });
    info.createEl("span", { text: "Continue writing", cls: "lk-resume-label" });
    info.createEl("div",  { text: last.file.name,     cls: "lk-resume-title" });
    info.createEl("div",  {
        text: `${last.file.folder} · ${when}`,
        cls: "lk-resume-meta"
    });
    const btn = card.createDiv({ cls: "lk-resume-cta" })
                    .createEl("button", { text: "Open scene →", cls: "lk-resume-btn" });
    btn.addEventListener("click", () =>
        app.workspace.openLinkText(last.file.path, "", false));
}
```

> [!lk-cards|2]
> ![[card-story.jpeg]]
> **[[Story]]**
>
> ![[card-notes.jpeg]]
> **[[Notes]]**

> [!lk-cards|2]
> ![[card-inprogress.jpeg]]
> **[[InProgress|In Progress]]**
>
> ![[card-map.jpeg]]
> **[[ExampleMap|Map]]**

## World

> [!lk-cards|6]
> ![[card-characters.jpeg]]
> **[[Character]]**
>
> ![[card-ancestry.jpeg]]
> **[[Ancestry]]**
>
> ![[card-organization.jpeg]]
> **[[Organization]]**
>
> ![[card-art.jpeg]]
> **[[Art]]**
>
> ![[card-settlement.jpeg]]
> **[[Settlement]]**
>
> ![[card-geography.jpeg]]
> **[[Geography]]**
>
> ![[card-poi.jpeg]]
> **[[POI|POI]]**
>
> ![[card-history.jpeg]]
> **[[History]]**
>
> ![[card-country.jpeg]]
> **[[Country]]**
>
> ![[card-lore.jpeg]]
> **[[Lore]]**
>
> ![[card-religion.jpeg]]
> **[[Religion]]**
>
> ![[card-concept.jpeg]]
> **[[Concept]]**
>
> ![[card-magic.jpeg]]
> **[[Magic]]**
>
> ![[card-object.jpeg]]
> **[[Object]]**
>
> ![[card-nature.jpeg]]
> **[[Nature]]**
>
> ![[card-technology.jpeg]]
> **[[Technology]]**
>
> ![[card-language.jpeg]]
> **[[Language]]**
>
> ![[card-misc.jpeg]]
> **[[Misc]]**

## Recent

```base
filters:
  and:
    - '!file.inFolder("Templates")'
    - '!file.inFolder("Archive")'
    - '!file.inFolder(".obsidian")'
    - file.ext == "md"
views:
  - type: table
    name: Recent Files
    order:
      - file.name
      - file.mtime
    sort:
      - property: file.mtime
        direction: DESC
    limit: 10
```

## Resources

> [!lk-links]
> - [[Documentation]]
> - [[Master Tags List]]
> - [[Quality Control Dashboard]]
> - [[Buttons]]
> - [[Notes|All Notes]]
> - [[Scratch Note]]
> - [[Excalidraw|All Excalidraw Notes]]
> - [[Images|All Images]]
