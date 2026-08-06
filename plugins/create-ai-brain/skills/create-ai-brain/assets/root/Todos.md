---
type: todos
tags: [system, todos]
---

# Todos

This is a **live dashboard**, not a manual list. Todos live wherever they came from — a meeting note, a daily note, a project note, a person note — with a due date attached. This page just queries the whole vault for anything still open, so completing a task here *or* at the source keeps both in sync (it's the same checkbox, just rendered twice).

Requires the **Tasks** community plugin — see `System/Todos Setup.md` if you haven't installed it yet.

## All open todos, soonest due first

```tasks
not done
sort by due
```

## Overdue

```tasks
not done
due before today
sort by due
```

## Due this week

```tasks
not done
due after today
due before in 7 days
sort by due
```

## Recently completed

Capped at the last 20 so this doesn't grow forever — full history lives in `Archives/`.

```tasks
done
sort by done reverse
limit 20
```

## Full history

Anything completed more than ~2 weeks ago gets swept out of this view and into a monthly log: `Archives/Todos Archive YYYY-MM.md`. The nightly consolidation prompt does this automatically — see `System/Nightly Consolidation Prompt.md`.
