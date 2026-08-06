# START HERE — Create AI Brain

This is a skill that builds you a personal "AI Brain": an Obsidian-style second-brain vault with a ready-made folder structure, four system prompts (meeting extraction, nightly consolidation, book processing, todos), note templates, and a short interview that writes your personal IDENTITY / USER / SOUL files.

Read this before running it — especially the part about **where** to run it.

## What you need

- **Cowork or Claude Code.** This skill runs *inside* one of those — it isn't a standalone installer you double-click. Install the skill there first (in Cowork, use the "Save skill" button on the `.skill` file).
- **Obsidian is optional.** The vault is just plain markdown files and folders, so it's fully readable and editable in any text editor, and the four prompts work through Claude regardless. But Obsidian is what makes it feel like a second brain: the `[[wiki-links]]` between notes become clickable navigation, and the `Todos.md` dashboard becomes a live, self-updating task list once you install the free **Tasks** community plugin. Without Obsidian, those links are just text and the todo dashboard won't run its queries. You can add Obsidian later — nothing needs redoing.

## Installing the skill

You install this once; after that it's available in every session. There are two files here that matter: the packaged `create-ai-brain.skill` (a zip) and the unzipped `create-ai-brain/` folder (which contains `SKILL.md`). Use whichever fits your setup.

**Cowork** — get the `create-ai-brain.skill` file (download it from the repo), then open a Cowork chat and add/upload that `.skill` file to the conversation. It renders with a **"Save skill"** button — click it. The skill is now saved to your account and persists across all future sessions.

**Claude Code** — copy the unzipped `create-ai-brain/` folder (the one with `SKILL.md` inside it) into one of your skills directories:
- `~/.claude/skills/create-ai-brain/` — available in every project on your machine, or
- `<your-project>/.claude/skills/create-ai-brain/` — available only in that project.

Then start (or restart) a Claude Code session and the skill will be picked up automatically.

To confirm it's installed, ask Claude "what skills do I have?" — `create-ai-brain` should be listed.

## How to run it (and where)

**The single most important thing: run it pointed at the exact folder where you want the vault to live.** The skill creates the whole structure *inside* whatever folder you give it, so picking the right one up front saves you moving things later.

1. Decide on (or create) an empty folder for your vault — e.g. `Documents/AI Brain`.
2. In Cowork, connect/select that folder. In Claude Code, open a session in that folder.
3. Say: **"Set up my AI Brain in this folder."**
4. The skill will **confirm the full folder path with you before creating anything** — check it's the folder you meant, then approve.
5. It builds the structure, then interviews you to draft your IDENTITY / USER / SOUL files. Answer honestly and specifically — those three files are what make the assistant actually sound like you.

If you point it at a folder that already contains a vault, it won't overwrite — it'll ask whether to fill in missing pieces or start somewhere else.

## After it's built

- Open the folder in Obsidian (optional but recommended) and install the **Tasks** plugin — steps are in `System/Todos Setup.md`.
- Anything named "Example …" is a sample you can delete once you've seen the format.
- Ask Claude to run the **Nightly Consolidation Prompt** at the end of a day to keep the vault clean and linked, or have it scheduled to run automatically.
