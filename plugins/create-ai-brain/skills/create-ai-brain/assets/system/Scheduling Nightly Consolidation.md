---
type: system
tags: [system, nightly, scheduling]
---

# Scheduling the Nightly Consolidation

The Nightly Consolidation Prompt (`System/Nightly Consolidation Prompt.md`) is written to run every evening. You can run it by hand, but the point of a self-maintaining vault is that it runs on its own. Pick whichever option matches how you use Claude.

Because the prompt scopes to "everything changed since the last run" (via the `last_run` timestamp in `System/Last Consolidation Run.md`), a missed night is harmless — the next run just has a wider catch-up window. So you don't need a bullet-proof scheduler; roughly-nightly is fine.

## Option A — Claude desktop app / Cowork (easiest, no terminal)

The desktop app can run tasks on a schedule for you. Just ask your assistant, in a session that has access to this vault:

> Run my nightly consolidation on this vault every evening at 10pm.

It registers a recurring scheduled task that fires on that cadence and runs the consolidation unattended, then leaves you the end-of-run summary to review. Adjust the time/cadence to taste ("every weekday at 6pm", "each morning at 7am", etc.). To change or stop it later, just ask ("reschedule my nightly consolidation to 9pm" / "stop the nightly consolidation task").

This is the recommended route if you're not living in a terminal.

## Option B — Claude Code CLI on a system scheduler

If you use the Claude Code CLI, run it in headless mode from your OS scheduler. Because `CLAUDE.md` auto-loads the vault context, the prompt itself can be short.

The core command (run from the vault root):

```bash
cd ~/path/to/your-vault && claude -p "Run the nightly consolidation routine exactly as described in System/Nightly Consolidation Prompt.md, then give me the end-of-run summary."
```

Unattended runs can't stop to ask you to approve each file edit, so pre-approve the tools the run needs — set the vault's `.claude/settings.json` permissions (or the equivalent permission-mode flag) so consolidation can read, write, and move files without prompting. Test the command once interactively before you schedule it, so you know it completes cleanly.

### macOS / Linux — cron

Edit your crontab (`crontab -e`) and add one line (10pm nightly, logging output):

```
0 22 * * * cd ~/path/to/your-vault && /usr/local/bin/claude -p "Run the nightly consolidation described in System/Nightly Consolidation Prompt.md" >> ~/vault-consolidation.log 2>&1
```

Use the full path to the `claude` binary (`which claude` to find it) — cron runs with a minimal `PATH`.

### macOS — launchd (fires even after the machine was asleep)

If you want a missed run to fire when the Mac wakes, use a launchd agent with `StartCalendarInterval` instead of cron. Create `~/Library/LaunchAgents/com.you.vault-consolidation.plist` with an hour/minute and a program that runs the same `cd … && claude -p …` command via `/bin/zsh -c`, then `launchctl load` it.

### Windows — Task Scheduler

Create a Basic Task, trigger Daily at your chosen time, action "Start a program" running your shell with the same `claude -p` command and the vault as the working directory.

## After a run

Every run updates the `last_run` timestamp in `System/Last Consolidation Run.md` automatically. Skim the end-of-run summary when you're next in the vault — that's where the consolidation surfaces anything it couldn't resolve on its own.
