# create-ai-brain

A Claude Code plugin marketplace hosting the **create-ai-brain** plugin — a skill that scaffolds a personal "AI Brain" second-brain vault and interviews you to write your IDENTITY / USER / SOUL files.

This one repo is both the marketplace and the plugin. The marketplace and the plugin share the name `create-ai-brain`, so the install command reads `create-ai-brain@create-ai-brain` (plugin @ marketplace).

## Install (Claude Code)

Add this marketplace, then install the plugin:

```
/plugin marketplace add Nic-Grunklee/create-ai-brain
/plugin install create-ai-brain@create-ai-brain
```

The first command accepts a GitHub `owner/repo`, a full Git URL, or a local path. After installing, if Claude Code says `Run /reload-plugins to activate`, run that.

Then, in a session pointed at (or with access to) the folder where you want your vault:

```
Set up my AI Brain in this folder.
```

The skill confirms the exact folder before creating anything, builds the structure, and runs the identity interview.

## Install (Claude desktop app / Cowork)

Use the plugin browser in the desktop app, or install the skill directly: grab `plugins/create-ai-brain/skills/create-ai-brain/`, zip it as a `.skill`, and use the **Save skill** button — see that skill's `START HERE.md` for the full walkthrough.

## What you get

An 8-area markdown vault (People, Projects, Decisions, Companies, Meetings, Daily, Knowledge, plus Capture / Clippings / Books / MOC / Archives / System), four system prompts (Meeting Extraction, Nightly Consolidation, Book Processing, Todos), note templates, a full Books pipeline, and the auto-loading `CLAUDE.md` / `AGENTS.md`. It's plain markdown and works anywhere; open it in Obsidian (with the Tasks plugin) for linking and the live todo dashboard.

## Publishing / updating

Push this repo to your public GitHub repository `Nic-Grunklee/create-ai-brain`, then share the two install commands above. When you change the skill, bump `version` in both `marketplace.json` and `plugins/create-ai-brain/.claude-plugin/plugin.json` and push — users pull it with `/plugin marketplace update create-ai-brain`.

## Repo layout

```
create-ai-brain/
├── .claude-plugin/
│   └── marketplace.json          # catalog: lists the create-ai-brain plugin
├── plugins/
│   └── create-ai-brain/
│       ├── .claude-plugin/
│       │   └── plugin.json        # plugin manifest
│       └── skills/
│           └── create-ai-brain/
│               ├── SKILL.md        # the skill instructions
│               ├── START HERE.md   # human-facing setup / install guide
│               ├── assets/         # templates, system prompts, loaders
│               └── reference/       # identity-interview guide
└── README.md
```
