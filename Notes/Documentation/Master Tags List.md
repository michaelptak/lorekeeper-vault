---
tags: Notes
status: Complete
related:
note_purpose: Documentation
story_title:
priority:
---
> [!lk-navbar]+ Navigation
> **Quick Links:** [[Documentation]] | [[Notes|All Notes]] | [[Home]]
> 
> [[#Story]] ([[#Plot]] · [[#Scene]])
> 
> **Core Worldbuilding:** [[#Concept]] | [[#History]] | [[#Timeline]] | [[#Lore]]
> 
> **Physical World:** [[#Nature]] | [[#Geography]] | [[#POI]] | [[#Settlement]]
> 
> **People & Society:** [[#Ancestry]] | [[#Character]] | [[#Art]]
>
> **Systems & Institutions:** [[#Country]] | [[#Language]] | [[#Organization]] | [[#Religion]]
>
> **Supernatural & Material:** [[#Magic]] | [[#Object]] | [[#Technology]]
>
> **Niche:** [[#Language]] | [[#Misc]]


# **`=this.file.name`**
> [!example]- Making Edits
> This is Obsidian. It is possible to change almost anything if you really want. Recommended Approach:
> 1. Always start with editing the respective template for permanent changes. Don't sweat changing old notes immediately, just update them as you go along.
> 	- There are 1-3 places the changes are necessary. 1. An input field in the Meta Data callout. 2. If applicable, a view under the infobox callout 3. The frontmatter if a default value is desired (Auto-populated by metadata input field though)
> 		- The syntax looks confusing at first but you can copy it or if you really don't understand sent it to AI
> 2. **Most** properties where you select an option from a dropdown menu, can be edited in Meta Bind -> Input Field Templates. This is convenient as it requires no changes in any template or any note.
> 	- Alt approach: Edit `.obsidian/plugins/obsidian-meta-bind-plugin/data.json`
> 
> Not recommended:
> - Changing the folder structure around (Hard-coded in many templater scripts. Adding new folders however is fine)
> - Renaming the property name itself (Might break some existing dataview/Bases queries. It's very doable but honestly pointless as these are not really something you are ever viewing)

## Default Properties
- **Generally come with every template**
- `tags` - Every category comes with one, but this is a good opportunity for simple, free form metadata organization. Feel free to go crazy with it.
- `status`
  - `Stub` - basic notes, no immediate development plans
  - `Planned` - ready to develop when time allows, higher priority than stubs
  - `WIP` - actively working on in near future
  - `Complete` - developed enough to be considered finished
  - `Archived` notes that are considered defunct, low quality, irrelevant, etc. 
    - Move to the "Archive" folder automatically using Templater 
- `related` 
  - Broadly link to any note if it doesn't fall under one of the usual properties.
  - Particularly useful for linking any note to a `concept` as this is a very broad category. Also great for research notes

## Universal Properties
- **Note: Not always applicable but used by many templates.**
- `art` image(s) associated with the note

## Categories (Tags)
### Notes
- **Notes** (catch-all for anything that isn't World, Story, Assets, Indexes, or Templates — brainstorming, research, to-dos, documentation, references, etc.)
  - `note_purpose` - free text field describing the note's purpose (e.g. Brainstorm, Research, Planning, Reference, Documentation)
  - `story_title` - text field for filtering on stories (optional)
  - `priority` - High, Med, Low

### Story
- **Story** (narrative planning and story development using your fictional world)
  - `story_title` - "Story Title" (e.g. "The Fellowship of the Ring")
  - `status` - existing universal 
  - `related` - existing universal
  
#### Plot
- **Plot** (story structure, arcs, conflicts, themes, and major story beats - all planning/outline work)
  - `story_title` - "Story Title" (e.g. "The Fellowship of the Ring")
  - `plot_type` - Free text field (Arc, Conflict, Theme, Outline, Beat)
  - `plot_scope` - Free text field (Story, Act, Chapter)
  - `plot_focus` - Free text field (Character Arc, World Conflict, Thematic Element)
  - `story_order` - Optional ordering for chapter outlines (e.g. "1.0" for Chapter 1)
  - `scenes` → links to **Scene** notes (the actual prose files)
  - `pov_character` → links to **Character** (if this plot element focuses on specific POV)
  - `involves_world` → links to **Character**, **Settlement**, etc.
    - This is a bit redundant with `related` - however the distinction specifically for story notes just makes intuitive sense to me 

#### Scene  
- **Scene** (individual scenes containing actual prose/story content)
  - `story_title` - "Story Title" (e.g. "The Fellowship of the Ring")
  - `story_order` - chapter.scene.beat format for sorting (e.g. "1.2.3" for Chapter 1, Scene 2, Beat 3)
    - First number determines chapter grouping in manuscript compilation
    - Full format enables precise ordering within chapters
  - `status` -existing universal
  - `revisions` - Number (tracks revision count, starts at 1)
  - `pov` - Free text field or link to **Character** (perspective for this scene)
  - `scene_outline` → link to **Plot** note (optional reference to planning document)
  - `related` - existing universal

### Core Worldbuilding Elements

#### Concept
(Immaterial ideas, rules, and effects that shape your world — themes, natural laws, philosophical frameworks, prophecies, and conditions like curses or diseases. Use sub-tags to distinguish: `#Condition, #Theme, #Natural-Law, #Philosophy, #Prophecy`)
- `associated_with` → links to **Religion**, **Magic**, **Country**, **Art** (what institutions/systems embody this concept)
- `affects` → links to **Ancestry**, **Nature**, **Character** (what/who is subject to this concept or condition)
- `caused_by` → links to **Magic**, **Object**, **Character**, **Nature** (source of a condition, or origin of an idea)
- `cured_by` → links to **Object**, **Magic**, **Character**, **Technology** (for conditions specifically)
- Everything else (concept type, scope, severity, duration, origin, awareness, truth status, transmission) → prose in the note body

#### History
(Major events, periods, eras, and recurring occasions that shape your world's timeline. Use `historical_scope` to distinguish scale.)
- `historical_scope` - Event, Period, Era, Recurring
  - Event = specific occurrences
  - Period = longer than an event but shorter than an era
  - Era = broader time periods (ages, epochs)
  - Recurring = events that happen repeatedly (like holidays)
- `involved_characters` → links to **Character**
- `involved_organizations` → links to **Organization**
- `involved_countries` → links to **Country**
- `locations` → links to **Settlement**, **POI**, **Geography**, **Country**
- `preceded_by` → links to **History** (predecessor events)
- `led_to` → links to **History** (successor events)
- `concurrent_with` → links to **History** (simultaneous events, or sub/parent events)
- `sources` → links to **Lore** (written accounts, records)
- Everything else (event type, scope, era name, significance) → prose in the note body

#### Lore
(Actual writings and primary sources from within the world itself — books, scrolls, inscriptions, oral traditions, prophecies. Use `document_type` to distinguish.)
- `document_type` - Historical, Religious, Personal, Legal, Scholarly, Literary, Technical, Propaganda, Prophetic
- `author` → links to **Character**
- `commissioned_by` → links to **Character**, **Organization**
- `languages` → links to **Language**
- `current_location` → links to **Settlement**, **POI**, **Organization**
- `mentions` → links to **Character**, **History**, **Geography**, etc. (what/who appears in the document)
- `contradicts` → links to other **Lore** (conflicting accounts)
- `supports` → links to other **Lore** (corroborating sources)
- Everything else (form, authenticity, preservation, access, original location) → prose in the note body

### Physical World
#### Nature
(All living things — animals, plants, fungi, and fantastical organisms. Use sub-tags to distinguish: `#Creature, #Plant, #Fungi, #Hybrid)`
- `rarity` - Common, Uncommon, Rare, Legendary, Extinct, Mythical
- `habitat` → links to **Geography**, **Settlement**, **POI**
- `produces` → links to **Object**
- `raised_by` → links to **Ancestry**, **Organization** (domesticated, cultivated, or farmed)
- `created_by` → links to **Character**, **Organization**, **Magic**
- Everything else (appearance, behavior, diet, size, lifecycle, special properties) → prose in the note body

#### Geography
(All geographical and cosmic features — landmasses, biomes, bodies of water, celestial objects. Use sub-tags to distinguish:` #Terrestrial, #Cosmos, etc.`)
- `jurisdiction` → links to **Country**
- `controlled_by` → links to **Organization**
- `settlements` → links to **Settlement** (towns/cities in this region)
- `notable_features` → links to **POI** (landmarks within this geography)
- `native_inhabitants` → links to **Ancestry**, **Nature** (who/what naturally lives here)
- `resources` → links to **Object** (what's found here)
- `associated_with` → links to **Religion**, **Magic**, **Lore**, **History** (cultural/narrative connections)
- Everything else (terrain, climate, habitability, size, visibility, significance, cosmic type) → prose in the note body

#### POI
(Points of Interest — ruins, landmarks, dungeons, shrines, natural wonders, and other notable locations.)
- `locations` → links to **Geography** (where this POI is found)
- `jurisdiction` → links to **Country**
- `controlled_by` → links to **Organization**
- `discovered_by` → links to **Character**, **Organization**
- Everything else (poi type, condition, access, significance) → prose in the note body
#### Settlement
(Towns, cities, villages, outposts, and other inhabited places.)
- `inhabitants` → links to **Ancestry**
- `notable_sites` → links to **POI** (important locations within)
- `locations` → links to **Geography** (where it's located)
- `jurisdiction` → links to **Country**
- `controlled_by` → links to **Organization**
- `rulers` → links to **Character**
- `founded_by` → links to **Character**, **Organization**, **Country**
- `trade_partners` → links to **Settlement**, **Country**
- `resources` → links to **Object** (what it produces, imports, or trades)
- Everything else (settlement size, type, prosperity, defense) → prose in the note body

### People & Society
#### Ancestry
(Often called "race" in most fantasy worlds like elf, dwarf, human, etc.)
- `homeland` → links to **Geography**, **Country** (where they originate)
- `languages` → links to **Language**
- `parent_ancestry` → links to **Ancestry** (evolutionary/magical origin)
- `notable_members` → links to **Character**
- `associated_deities` → links to **Character**, **Religion**
- `art_forms` → links to **Art** (cultural art forms practiced by this ancestry)
- Everything else (lifespan, build, origin, physical traits, culture, customs) → prose in the note body

#### Character
- `role` - Protagonist, Antagonist, Mentor, Ally, Neutral
- `life_status` - Alive, Dead, Unknown, Undead
- `aliases` - text field (alternate names, titles)
- `age` - text field
- `ancestry` → links to **Ancestry**
- `organization` → links to **Organization**
- `location` → links to **Settlement**, **POI**, **Geography**, **Country** (current location)
- `family` → links to other **Character** (relatives, lovers, companions)
- `allies` → links to other **Character**
- `enemies` → links to other **Character**
- `owns` → links to **Object** (important possessions)
- `knows_magic` → links to **Magic**
- `follows_religion` → links to **Religion**
- `involved_in` → links to **History** (significant events they participated in)
- `conditions` → links to **Concept** (curses, blessings, diseases, etc.)
- Everything else (gender, profession, social class, hometown, appearance, personality, backstory) → prose in the note body

#### Art
(Cultural expressions, traditions, and art forms — visual arts, music, literature, crafts, ceremonies, martial traditions, etc.)
- `associated_ancestry` → links to **Ancestry** (which people practice this)
- `locations` → links to **Settlement**, **POI**, **Geography**, **Country** (Where its found)
- `influenced_by` → links to other **Art**
- `patron` → links to **Character**, **Organization**
- `practitioners` → links to **Character**, **Organization** (who practices this art/culture)
- `associated_religion` → links to **Religion** (religious traditions tied to this art form)
- `core_concepts` → links to **Concept** (thematic ideas behind it)
- Everything else (art type, medium, cultural focus, era, vitality) → prose in the note body

### Systems & Institutions
#### Country
(Nations, kingdoms, empires, city-states — any sovereign political entity)
- `capital` → links to **Settlement**
- `rulers` → links to **Character**
- `major_cities` → links to **Settlement**
- `territory` → links to **Geography** (lands controlled)
- `allies` → links to other **Country**
- `enemies` → links to other **Country**
- `vassals` → links to other **Country** (subordinate states)
- `overlord` → links to **Country** (if vassal of another)
- `inhabitants` → links to **Ancestry**
- `official_religion` → links to **Religion**
- `languages` → links to **Language** (official/common languages)
- Everything else (government type, size, wealth, stability, military power, economy) → prose in the note body
#### Language
(Spoken and written languages of your world — from common tongues to ancient scripts and magical languages)
- `spoken_by` → links to **Ancestry**, **Organization**, **Country**
- `related_languages` → links to other **Language**
- `derived_from` → links to **Language** (parent language)
- `written_works` → links to **Lore**
- `locations` → links to **Settlement**, **POI**, **Geography**, **Country** (where it's spoken)
- Everything else (usage, script type, language family, prevalence) → prose in the note body

#### Organization
(Guilds, orders, factions, companies, and any structured group with shared purpose.)
- `headquarters` → links to **Settlement**, **POI**, **Geography**, **Country**
- `leader` → links to **Character**
- `members` → links to **Character**
- `founded_by` → links to **Character**, **Organization**
- `allies` → links to **Organization**, **Country**
- `rivals` → links to **Organization**, **Country**
- `operates_in` → links to **Country**, **Settlement**, **Geography**
- `controls` → links to **Settlement**, **POI**, **Geography**, **Object**
- `associated_religion` → links to **Religion**
- Everything else (org type, scope, secrecy, size, influence) → prose in the note body

#### Religion
(Belief systems, faiths, cults, and spiritual traditions that shape cultures and characters.)
- `deities` → links to **Character** (gods/divine figures)
- `practiced_by` → links to **Ancestry**, **Country**, **Organization**
- `holy_sites` → links to **POI**, **Settlement**, **Geography**, **Country**
- `sacred_objects` → links to **Object**
- `sacred_texts` → links to **Lore**
- `religious_leaders` → links to **Character** (mortal clergy/leaders)
- `core_concepts` → links to **Concept**
- `associated_magic` → links to **Magic**
- `rival_religions` → links to **Religion**
- Everything else (belief type, influence level, organizational structure, primary focus) → prose in the note body

### Supernatural & Material
#### Magic
(Magic systems, disciplines, techniques, spells, and enchanted items — anything supernatural or arcane in your world.)
- `power_source` → links to **Concept**, **Geography** (where the magic draws power from)
- `practiced_by` → links to **Ancestry**, **Organization**, **Character**, **Religion**
- `requires` → links to **Object**, **Concept**, **Technology** (materials, conditions, or knowledge needed)
- `taught_at` → links to **Organization**, **Settlement**, **POI**
- `enables` → links to **Object**, **Magic**, **Concept**, **Technology** (what this magic makes possible)
- `countered_by` → links to **Magic**, **Object**, **Concept**, **Technology** (what opposes or nullifies it)
- Everything else (magic scope, type, learning method, societal view, rarity) → prose in the note body

#### Object
(All physical items and resources — weapons, tools, artifacts, raw materials, trade goods. Use sub-tags to distinguish: `#Resource, #Artifact`)
- `rarity` - Common, Uncommon, Rare, Unique, Legendary
- `creator` → links to **Character**, **Organization**
- `current_owner` → links to **Character**, **Organization**
- `located_at` → links to **Settlement**, **POI**, **Geography** (where it is now / where it's found)
- `made_from` → links to **Object** (materials/components — resources are objects too)
- `required_for` → links to **Object**, **Magic**, **Technology** (what needs this material/component)
- `associated_with` → links to **History**, **Character**, **Religion**, **Lore**, **Magic** (narrative connections)
- Everything else (object type, condition, significance, value, renewability, primary use, enchantments) → prose in the note body

#### Technology
(Inventions, techniques, engineering systems, and crafting methods — distinct from individual objects.)
- `created_by` → links to **Ancestry**, **Organization**, **Character**, **Country**
- `requires` → links to **Object**, **Magic** (materials or magic needed)
- `replaces` → links to **Technology**
- `enables` → links to **Object**, **Magic**, **Concept**, **Technology** (what this tech makes possible)
- `discovered_at` → links to **Settlement**, **POI**, **Country**, **Geography**
- `used_by` → links to **Ancestry**, **Organization**, **Character**, **Country**
- `documentation` → links to **Lore**
- Everything else (tech stage, availability, tech type, complexity) → prose in the note body

#### Misc
(Catch-all for worldbuilding notes that don't fit any other category. Use when nothing else applies.)
- `related` - existing universal