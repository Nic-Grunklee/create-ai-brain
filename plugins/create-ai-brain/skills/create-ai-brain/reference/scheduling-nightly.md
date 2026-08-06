# Setting up the nightly consolidation to run on a schedule

This is guidance for whoever is setting up the vault — it is **not** copied into the vault. Use it during Step 7 of the skill when the owner wants the Nightly Consolidation Prompt to run automatically. The prompt itself lives in the vault at `System/Nightly Consolidation Prompt.md`.

Because the prompt scopes to "everything changed since the last run" (via the `last_run` timestamp in `System/Last Consolidation Run.md`), a missed night is harmless — the next run just has a wider catch-up window. So a roughly-nightly schedule is plenty; it doesn't need to be bullet-proof.

## Option A — Claude desktop app / Cowork (easiest, no terminal)

The desktop app can run tasks on a schedule. Set up a recurring scheduled task that, each evening, runs the Nightly Consolidation Prompt against this vault and leaves the end-of-run summary for review. Do this for the owner rather than just describing it — confirm a time/cadence ("every evening at 10pm", "each weekday at 6pm", "each morning at 7am") and register it. Tell them how to change or stop it later (just ask their assistant to reschedule or cancel the task).

This is the default route for anyone not living in a terminal.

## Option B — Claude Code CLI on a system scheduler

If they use the Claude Code CLI, run it in headless mode from their OS scheduler. Because `CLAUDE.md` auto-loads the vault context, the prompt can be short.

Core command (run from the vault root):

```bash
cd ~/path/to/your-vault && claude -p "Run the nightly consolidation routine exactly as described in System/Nightly Consolidation Prompt.md, then give me the end-of-run summary."
```

Unattended runs can't stop to approve each edit, so pre-approve the tools the run needs — set the vault's `.claude/settings.json` permissions (or the equivalent permission-mode flag) so consolidation can read, write, and move files without prompting. Have them test the command once interactively before scheduling it.

- **macOS / Linux (cron):** `crontab -e`, then a nightly line using the full path to `claude` (cron has a minimal `PATH` — find it with `which claude`):

  ```
  0 22 * * * cd ~/path/to/your-vault && /usr/local/bin/claude -p "Run the nightly consolidation described in System/Nightly Consolidation Prompt.md" >> ~/vault-consolidation.log 2>&1
  ```

- **macOS (launchd):** for a run that fires after the Mac wakes from sleep, use a `~/Library/LaunchAgents/*.plist` with `StartCalendarInterval` running the same `cd … && claude -p …` command via `/bin/zsh -c`, then `launchctl load` it.

- **Windows (Task Scheduler):** a Basic Task, trigger Daily, action "Start a program" running the shell with the same `claude -p` command and the vault as the working directory.

## If they decline

Don't leave anything behind in the vault. Just tell them they can run `System/Nightly Consolidation Prompt.md` by hand any time, and that they can ask you to set up the automatic schedule whenever they want it later.
