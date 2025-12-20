---
tags: Meta
status: Complete
related:
purpose: Vault
priority:
project_id:
---
> [!metadata]- Meta Data
> #### General
>  |
> ---|---|
> **Tags** | `INPUT[Tags][inlineListSuggester:tags]` |
> **Status** | `INPUT[select(option(Stub), option(Planned), option(WIP), option(Complete)):status]` |
> **Related** | `INPUT[inlineListSuggester(optionQuery("" AND !"Templates"), useLinks(partial)):related]` |
> 
> #### Meta Properties
>  |
> ---|---|
> **Purpose** | Vault |
> **Priority** | `INPUT[select(option(High), option(Med), option(Low)):priority]` |
> **Project ID** | `INPUT[text:project_id]` |
# **`=this.file.name`**
# Strategy/Tips
- **Avoid using folder navigation for the most part, unless you are working on a Story or something related to the vault like Templates** 
	- Navigate from the Home Page. Accessed multiple places on the left file navigation or far left sidebar icon.
		- Can always `CTRL+O` search for "Home"
	- Use links:  typing open brackets `[[` will allow automatically selecting notes to create links
	- Templates - I use templater scripts to make these move to the right directory anyways:
		- `ALT+N` (create new note + insert template) generally recommended way, it prompts you for the name that way
		- `ALT+T` (insert into existing note)
		- Buttons: These are just convenient ways to insert templaters templates
	- Direct search: `CTRL+O` hotkey
	- Obsidian Bases:
		- Refer to the index to indexes (to-do)
		- `CTRL+P` insert new base and utilize filters to granularize
- **Where to use folders**
	- `Assets` folder:
		- You can't add text metadata to images, which is why there is a greater folder structure here, so you can granularize using bases still.
		- New attachments will just drop into the assets folder root directory, need to drop them into respective selector for inline selectors to work
		- `ALT+M` hotkey helps here to make this more efficient
	- `Bases`: Drag and drop if creating new base. Unfortunately they dont have a setting for default folder (yet)

# Category Explanations
- **Note** For more on Worldbuilding categories [[Master Tags List]]
- **World/** - The fictional universe as it exists independently of any story. These notes answer "What is true in this world?" regardless of narrative presentation.
- **Story/** - How you plan to present and use your world in narrative form. Links heavily to World/ notes but focuses on plot, pacing, and \*reader experience.
	- \*Note: If used as a TTRPG vault I think this section should also be used. After all a TTRPG is just another form of narrative
- **Meta/** - Real-world workflow, research, and vault management. Everything related to the process of creating rather than the creation itself.

# Folder Structure Tree (important info)
```css
Root Directory/
├── Assets/                    # Media files and images
│   ├── Banners/              # Decorative headers for notes
│   ├── Icons/                # Small graphics for visual organization
│   ├── Maps/                 # World maps and geographical references
│   ├── MetaImg/              # Images for vault management and templates
│   ├── TemplateImg/          # Default images used in note templates
│   ├── Reference/            # Real-world reference images organized by category
│   └── WorldImg/             # Images depicting fictional world elements
├── Archive/                   # Deprecated or low-quality notes automatically moved here
├── Bases/                     # Database-style index notes using Obsidian Bases
├── Drawings/                  # Excalidraw diagrams, mind maps, and sketches
├── Meta/                      # Vault management and real-world workflow
│   ├── Brainstorm/           # Raw idea generation and free-form thinking
│   ├── Inspiration/          # External sources, quotes, and creative influences
│   ├── Planning/             # Project management, tasks, and writing schedules
│   ├── Project/              # Multi-note project coordination and tracking
│   ├── Reference/            # External resources and research materials
│   ├── Research/             # Information gathering and analysis
│   └── Vault/                # Obsidian-specific configuration and maintenance
├── Story/                     # Narrative planning and story development
	├── Example story/        # Project directory for a story
	│   ├── Plot/                 # Story structure, arcs, conflicts, and themes
	│   └── Scene/                # Individual scenes with actual prose
├── Templates/                 # Automated note creation and formatting
│   ├── T_Actions/            # Templater automation scripts
│   ├── T_Meta/               # Templates for vault management notes
│   ├── T_Snippets/           # Reusable content blocks
│   ├── T_Story/              # Templates for narrative planning notes
│   ├── T_World/              # Templates for worldbuilding elements
│   └── z_Scripts/            # Advanced automation and custom functions
└── World/                     # The fictional universe itself
│   ├── Timeline/              # Unique category for timelines
    └── [All worldbuilding categories organized by type]
├── Home (note)               # Vault entry point and navigation hub
```

# Folder Structure Tree (FULL)
```css
Root Directory/
├── Assets/
│   ├── Banners/
│   ├── Icons/
│   ├── Maps/
│   ├── MetaImg/
│   ├── TemplateImg/
│   ├── Reference/
│   │   ├── Ancestry/
│   │   ├── Character/
│   │   ├── Condition/
│   │   ├── Concept/
│   │   ├── Cosmos/
│   │   ├── Country/
│   │   ├── Creature/
│   │   ├── Culture-Art/
│   │   ├── Economy/
│   │   ├── Flora/
│   │   ├── Geography/
│   │   ├── History/
│   │   ├── Language/
│   │   ├── Lore/
│   │   ├── Magic/
│   │   ├── Object/
│   │   ├── Organization/
│   │   ├── POI/
│   │   ├── Politics/
│   │   ├── Religion/
│   │   ├── Resource/
│   │   ├── Settlement/
│   │   └── Technology/
│   └── WorldImg/
│       ├── Ancestry/
│       ├── Character/
│       ├── Condition/
│       ├── Concept/
│       ├── Cosmos/
│       ├── Country/
│       ├── Creature/
│       ├── Culture-Art/
│       ├── Economy/
│       ├── Flora/
│       ├── Geography/
│       ├── History/
│       ├── Language/
│       ├── Lore/
│       ├── Magic/
│       ├── Object/
│       ├── Organization/
│       ├── POI/
│       ├── Politics/
│       ├── Religion/
│       ├── Resource/
│       ├── Settlement/
│       └── Technology/
├── Archive/
├── Bases/
├── Drawings/
├── Meta/
│   ├── Brainstorm/
│   ├── Inspiration/
│   ├── Planning/
│   ├── Project/
│   ├── Reference/
│   ├── Research/
│   └── Vault/
├── Story/
├── Templates/
│   ├── T_Actions/
│   ├── T_Meta/
│   ├── T_Snippets/
│   ├── T_Story/
│   ├── T_World/
│   └── z_Scripts/
└── World/
    ├── Ancestry/
    ├── Character/
    ├── Condition/
    ├── Concept/
    ├── Cosmos/
    ├── Country/
    ├── Creature/
    ├── Culture-Art/
    ├── Economy/
    ├── Flora/
    ├── Geography/
    ├── History/
    ├── Language/
    ├── Lore/
    ├── Magic/
    ├── Object/
    ├── Organization/
    ├── POI/
    ├── Politics/
    ├── Religion/
    ├── Resource/
    ├── Settlement/
    ├── Technology/  
    └── Timeline/
├── Home (note)
```