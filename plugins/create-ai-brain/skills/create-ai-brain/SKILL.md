---
name: create-ai-brain
description: Sets up a personal "AI Brain" — an Obsidian second-brain vault with a fixed folder structure, four system prompts (meeting extraction, nightly consolidation, book processing, todos), templates, and a live identity interview that drafts the owner's IDENTITY / USER / SOUL files. Use whenever someone wants to create, scaffold, set up, or bootstrap an AI Brain, second brain, personal knowledge vault, or "Dan Martell style" note system — or asks to (re)run the identity interview for their USER/SOUL/IDENTITY files. Don't use for editing notes inside a vault that already exists.
---

# Create AI Brain

This skill scaffolds a complete personal AI Brain vault from scratch and runs an interview to write the three identity files that make it personal. It's designed to be shared — nothing in it is tied to any one person; the identity comes entirely from the interview.

The vault is an Obsidian vault, but nothing here depends on Obsidian being installed — it's just markdown files and folders. The only Obsidian-specific piece is the optional **Tasks** plugin, which powers the live `Todos.md` dashboard (covered in `System/Todos Setup.md`).

## What gets built

A fixed 8-area structure plus supporting files:

- `People/` `Projects/` `Decisions/` `Companies/` — one file per entity
- `Meetings/` `Daily/` — raw notes and day logs
- `Knowledge/` — atomic, reusable notes, indexed by `Knowledge/_Index.md`
- `Capture/` — zero-friction inbox for links/ideas; nightly consolidation sorts it
- `Clippings/` — raw web-clipper output, one step upstream of `Capture/`
- `Books/` — permanent per-book notes with a full processing pipeline (Notes → My Takeaways → AI Notes → Derived notes → For future writing)
- `MOC/` — Maps of Content, built only when a topic gets messy
- `Archives/` — processed captures, consumed clips, old completed todos
- `System/` — the four system prompts and the consolidation timestamp
- Root: `CLAUDE.md` + `AGENTS.md` (auto-loaders), `IDENTITY.md` / `USER.md` / `SOUL.md`, `Todos.md`, `Ideas to Try.md`

All templates, prompts, and loader files ship inside this skill under `assets/`. The interview writes the three identity files fresh.

## Steps

### 1. Pick the vault location — and confirm it explicitly

This is the step most likely to go wrong, so slow down here. The vault gets built *inside* whatever folder you're given, so it must be the folder the owner actually intends.

- Ask where the vault should live and what to call it (default folder name: `AI Brain`).
- If you don't yet have write access to that location, request it.
- **Echo the full absolute path back and get an explicit yes before creating anything** — e.g. "I'll create the vault at `/Users/…/Documents/AI Brain` — is that the right folder?" Don't assume the current working directory is correct; the owner may have opened the session somewhere else.
- Check whether a vault already exists there (look for `CLAUDE.md` or the `System/` folder). If it does, don't overwrite — ask whether to fill in missing pieces or start fresh elsewhere.

### 2. Create the folder structure

Create these folders under the vault root:

```
People  Projects  Decisions  Companies  Meetings  Daily
Knowledge  Capture  Clippings  Books  MOC  System
Archives  Archives/Capture  Archives/Clippings
```

### 3. Copy the bundled files into place

Copy every file from this skill's `assets/` directory into the vault, keeping the exact filenames. Map them like this:

| From (in this skill) | To (in the vault) |
|---|---|
| `START HERE.md` (this skill's root) | `START HERE.md` |
| `assets/root/CLAUDE.md` | `CLAUDE.md` |
| `assets/root/AGENTS.md` | `AGENTS.md` |
| `assets/root/Todos.md` | `Todos.md` |
| `assets/root/Ideas to Try.md` | `Ideas to Try.md` |
| `assets/templates/Book Template.md` | `Books/Book Template.md` |
| `assets/templates/Capture Template.md` | `Capture/Capture Template.md` |
| `assets/templates/Meeting Template.md` | `Meetings/Meeting Template.md` |
| `assets/templates/Person Template.md` | `People/Person Template.md` |
| `assets/templates/Todos Archive Template.md` | `Archives/Todos Archive Template.md` |
| `assets/system/Meeting Extraction Prompt.md` | `System/Meeting Extraction Prompt.md` |
| `assets/system/Nightly Consolidation Prompt.md` | `System/Nightly Consolidation Prompt.md` |
| `assets/system/Book Processing Prompt.md` | `System/Book Processing Prompt.md` |
| `assets/system/Todos Setup.md` | `System/Todos Setup.md` |
| `assets/system/Last Consolidation Run.md` | `System/Last Consolidation Run.md` |
| `assets/knowledge/_Index.md` | `Knowledge/_Index.md` |

Don't rewrite these files' contents — copy them verbatim. They reference each other by path, so the names matter.

### 4. Run the identity interview

This is the important part — it's what makes the vault personal. Open `reference/identity-interview.md` in this skill and follow it: interview the owner about how they work, what they value, how they communicate, and what they want from an AI assistant. Ask a few questions at a time, follow up when answers are thin or generic, and keep pushing until the material is specific.

Then draft `IDENTITY.md`, `USER.md`, and `SOUL.md` using the formats in that reference file. Show the drafts, invite edits, and only write the final versions into the vault root once the owner is happy. These three files are read at the start of every session, so keep them tight and concrete.

### 5. Personalize the loaders (optional)

`CLAUDE.md` and `AGENTS.md` are written generically ("the vault owner"). If the owner wants, swap in their name. Everything else in them is structural and stays as-is.

### 6. Explain the workflows and offer automation

Give a short tour of the four routines so they know what they now have:

- **Meeting Extraction** (`System/Meeting Extraction Prompt.md`) — run on raw meeting notes to pull decisions, commitments, preferences, insights.
- **Nightly Consolidation** (`System/Nightly Consolidation Prompt.md`) — the main maintenance pass: dedupes, links, creates orphan notes, extracts todos with due dates, processes `Capture/`, archives old todos. Can be run manually or on a schedule.
- **Book Processing** (`System/Book Processing Prompt.md`) — run after finishing a book to shortlist ideas worth promoting into `Knowledge/` and seed blog-post angles.
- **Todos** (`Todos.md` + `System/Todos Setup.md`) — a live dashboard; requires the Obsidian **Tasks** plugin (one-minute install, steps in the setup file).

Point out that files/folders prefixed with "Example" are illustrative and safe to delete, but their format should be matched when creating real notes. Then offer to schedule the nightly consolidation as a recurring evening task so the vault self-maintains, and offer to walk them through installing the Tasks plugin.

## Design principles (keep these intact)

- **The AI surfaces candidates; the owner curates.** Book ideas and capture promotions are shortlisted for review, never auto-committed to `Knowledge/`.
- **Capture is zero-friction.** Don't decide where something belongs at write time — that's the nightly run's job.
- **Keep it simple.** Don't add folders, plugins, or automation beyond what's documented unless asked. The structure is deliberately minimal.
