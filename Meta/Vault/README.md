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

> [!info|no-i collapse bg-c-gray callout-bordered ttl-c txt-c] Navigation
> [[Obsidian-Vault.base|Vault Notes]] | [[Meta.base|All Meta Notes]] | [[Home]]
# **`=this.file.name`**
## Note
This vault is not beginner friendly if you want to make your own templates and categories that aren't include in my current system. I did my best to make the system as comprehensive as possible, and to automate as much as I can.

If you ever want to view all the meta notes related to how the vault is set up, check out:
[[Obsidian-Vault.base]]

## Essentials
### View Mode / Live Preview Mode / Source Mode
- **View Mode**
	- I have this set to be the default view. Great for aesthetics, navigation, and setting meta data in the top call out.
- **Live Preview Mode**
	- `CTRL+E` to enable editing mode.
	- Default preview method that renders the note and edit at the same time.
	- Works great for most use cases: Some right-aligned elements like infoboxes do not work well in it. However, in my set up its not good practice to directly edit these anyways (they are mostly filled out by note metadata)
- **Source Mode** 
	- `ALT+S` once you are in edit mode to enter.
	- This can be nice when editing syntax heavy notes.
- **Change Default Mode** in Settings > Editor

## Navigating the Vault
[[Obsidian Vault Navigation Guide]]

## Understanding the categories (on of the most important to reference)
[[Master Tags List]]

## Date & Time, Calendars and Timelines
This will probably be one of the most steep learning curves, because it really isn't possible for me to make this customizable without digging into the plugin settings. However, the History and Timeline templates should be still very versatile with any setup, you just have to create the calendar and maybe mess with date formatting until you like it.
**Step 1.** Go to plugin settings and to `Calendarium`.  Create the calendar for your world, this part is very flexible. You can make different calendars for different cultures or eras if you want, but just keep in mind each note can only be tied to one calendar (It can, however, be tied to any amount of timelines). So I really just recommend creating one global calendar to start.
**Step 2.** Have a look at the master list and the relevant properties for History and Timeline. These are all that you need to fill out in order to automatically populate. The date format is technically possible to change in April's Automatic Timeline's, but I am unsure if you can with calendars.
**Step 3.** I've created a default [[World History Timeline]] that i recommend keep, as well as a randomly generated [[Succession of Kingdom of Valor]] timeline that you can use as reference (Manually delete these from the World/History folder and the individual timeline when you're done.
**Step 4**. Insert a History_Timeline template to create a timeline yourself. Create your own notes and go crazy with it. 
>[!note] Recommendation
> Do not use Calendarium for anything other than setting the structure of your world calendar.
> Why? Because for some reason getting it to automatically manage events has been very inconsistent for me, and all around I found (personally) harder to use and less visually appealing. 
> Just a personal recommendation but I think you should treat it more as a set-it-and-forget-it aspect of the vault than trying to manage it.