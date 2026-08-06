---
type: system
tags: [system, claude-code]
---

# AI Brain — Read This First

This file loads automatically at the start of every Claude Code session in this vault. Do the following before responding to anything else:

1. Read `IDENTITY.md`, `USER.md`, and `SOUL.md` in this root. They define who the vault owner is, how they work, what they value, and how you should communicate with them (direct, concise, no fluff, opinions backed by frameworks).
2. Read `System/Last Consolidation Run.md` to know how current the vault is.

## Vault structure

- `People/` — one file per person, context + things to remember + follow-ups
- `Projects/` — one file per project, timestamped, with goal/timeline/related links
- `Decisions/` — what was decided, alternatives considered, why
- `Companies/` — vendors, clients, competitors — research and notes
- `Meetings/` — raw notes + extracted decisions/commitments/preferences/insights + todos
- `Daily/` — one file per day, 3-5 line dump of what happened
- `Knowledge/` — atomic notes on frameworks, insights, quotes worth reusing; see `Knowledge/_Index.md`
- `Capture/` — one file per raw capture (video, article, podcast, stray idea) — zero-friction, don't decide where it belongs at write time. Nightly consolidation distributes its content elsewhere and moves the processed file into `Archives/Capture/`. See `Capture/Capture Template.md`.
- `Clippings/` — raw web-clipper output (the upstream inbox one step before `Capture/`). A clip lives here until its content has been pulled into a Capture/Knowledge note; once consumed, it moves to `Archives/Clippings/`. So `Clippings/` = clips not yet turned into anything.
- `Books/` — one file per book, permanent (never deleted/moved): Notes (raw capture) → My Takeaways (your own concise ones) → AI Notes (synopsis + deep takeaways) → Derived notes → For future writing. See `Books/Book Template.md` and `System/Book Processing Prompt.md`.
- `MOC/` — Maps of Content; only build one when a topic gets messy enough to need consolidating, not by default
- `Archives/` — completed todos older than ~2 weeks (filed by month), processed captures (`Archives/Capture/`), and consumed web clips (`Archives/Clippings/`)
- `System/` — the prompts and mechanics below
- `Todos.md` — a live Tasks-plugin dashboard querying the whole vault; never add todos here directly, add them at the source note
- `Ideas to Try.md` — a running backlog of small, concrete workflow experiments worth trying (work + personal), sourced from captures/knowledge notes. Not a todo list — no due dates, not on the Todos dashboard. Check items off with an outcome note when tried, don't delete them.

Files/folders prefixed with "Example" are fake illustrative notes — ignore them as real content, but match their format when creating real ones.

## System prompts

- `System/Meeting Extraction Prompt.md` — run against raw meeting notes to pull out decisions, commitments, preferences, key insights.
- `System/Nightly Consolidation Prompt.md` — the main maintenance routine: catches up on everything changed since `System/Last Consolidation Run.md`'s timestamp (not just "today"), finds orphan notes, dedupes, updates MOCs, extracts todos with due dates, archives old completed todos, links new Knowledge notes via `Knowledge/_Index.md`, and processes anything sitting unprocessed in `Capture/`. Run manually when asked; not currently scheduled.
- `System/Todos Setup.md` — Tasks plugin reference (due date syntax, dashboard queries, archiving flow).
- `System/Book Processing Prompt.md` — run on-demand (not nightly) after finishing a book: shortlists ideas worth promoting from a `Books/` note into atomic `Knowledge/` notes. Ideas are curated by the owner, never auto-promoted.

## Ground rules

- Be direct and concise. No fluff, no hedging. Back opinions with reasoning or a framework, not just an assertion.
- When processing meetings interactively, ask before deciding anything ambiguous or strategic rather than guessing silently. The nightly consolidation run is the exception: it moves things as it sees fit without gating on approval and ends with a concise bulleted summary for review (see `System/Nightly Consolidation Prompt.md`), only surfacing a decision when it genuinely can't be resolved autonomously.
- Keep changes proportional — don't add new folders, plugins, or automation beyond what's already documented here unless asked. This vault is deliberately kept simple.
