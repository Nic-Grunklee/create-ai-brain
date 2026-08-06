# create-ai-brain (plugin)

Bundles the **create-ai-brain** skill. Installed via the marketplace in this repo:

```
/plugin marketplace add Nic-Grunklee/create-ai-brain
/plugin install create-ai-brain@create-ai-brain
```

(The marketplace and plugin share the name `create-ai-brain`, so the install reads `create-ai-brain@create-ai-brain`.)

The skill lives at `skills/create-ai-brain/`. Its `START HERE.md` explains prerequisites (Cowork or Claude Code; Obsidian optional) and how to run it. Everything the skill writes into a new vault ships under `skills/create-ai-brain/assets/`, and the identity-interview guide is in `skills/create-ai-brain/reference/`.

All file references inside the skill are relative to the skill directory, so the plugin works after being copied into Claude Code's plugin cache.
