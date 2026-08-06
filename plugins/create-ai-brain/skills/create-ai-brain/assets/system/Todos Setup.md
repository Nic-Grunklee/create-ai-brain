---
type: system
tags: [system, todos, setup]
---

# Todos Setup — Tasks Plugin

Obsidian's native checkboxes don't support due dates or cross-file linking on their own. The **Tasks** community plugin adds both:

- Due dates and other metadata via emoji shorthand, e.g. `- [ ] Follow up with Jane 📅 2026-07-16`
- A query block (` ```tasks ` ) that pulls every open task from across the whole vault into one view, sorted/filtered however you like
- Because the query is a *live view of the actual checkbox*, checking a task off in the dashboard (Todos.md) checks it off in the source note too, and vice versa — there's only one underlying checkbox, not a copy

## Install it (one-time, ~1 minute)

1. Obsidian Settings → **Community plugins** → turn off Restricted mode if it's still on.
2. Click **Browse**, search **"Tasks"** (by schemar).
3. Install, then enable it.
4. Optional but recommended: also install **Dataview** — useful later if you want custom queries beyond what Tasks covers (e.g. "show me all open todos linked to a specific person").

No configuration needed beyond that — default settings work fine.

## Syntax cheat sheet

| What | Syntax |
|---|---|
| Due date | `📅 2026-07-16` |
| Scheduled date | `⏳ 2026-07-14` |
| Priority (high) | `⏫` |
| Recurring | `🔁 every week` |
| Done | Obsidian fills in `✅ 2026-07-16` automatically when checked |

Example: `- [ ] Send updated rate-limit docs to Jane 📅 2026-07-11 ⏫`

## Where todos should actually live

Write the todo where it was generated — a meeting note, a daily note, a project note, a person note — not directly in Todos.md. Todos.md just queries all of them. This is also what the nightly consolidation prompt now does automatically (see `System/Nightly Consolidation Prompt.md`).

## Keeping completed todos from piling up

Three layers, so nothing grows unbounded:

1. Todos.md only shows "Recently completed" (capped at the last 20 via a `limit 20` query) — not every completed task ever.
2. Anything completed more than ~2 weeks ago gets moved by the nightly consolidation prompt out of its source note and into `Archives/Todos Archive <YYYY-MM>.md` — one file per month.
3. Source notes (meetings, projects, etc.) stay lean since old completed items don't linger in them forever.

If you ever want to search the full history, it's all in `Archives/` — or run a `tasks` query with `done` and no `limit` to see everything not yet archived.
