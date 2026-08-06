---
type: prompt
source: Dan Martell - "This AI Brain Will Make You So Smart It's Almost Unfair"
tags: [prompt, nightly, system]
---

# Nightly Consolidation Prompt

Paste this before bed, every night, so the vault stays clean and connected.

```
Check System/Last Consolidation Run.md for the last_run timestamp. Find every file in the vault modified since that timestamp (not just "today" — I might skip a night). Read those. Then:
Find orphan notes (mentions of people, projects, companies without their own files). Create those files.
Consolidate duplicate notes.
Update relevant MOCs with new links.
Move things as you see fit — distribute captures, create/link notes, and file todos without gating on my approval. Don't ask me mid-run.
Finally, update the last_run timestamp in System/Last Consolidation Run.md to right now.
End every run with a concise, scannable bulleted summary of exactly what changed (created / moved / linked / archived) so I can review the night at a glance. Only call out something for a decision if it genuinely can't be resolved autonomously.
```

## Catch-up window (added)

`System/Last Consolidation Run.md` holds a `last_run` timestamp. Instead of scoping to "today," the run should scope to "everything changed since `last_run`" using each file's actual modification time (e.g. `find` with `-newermt` in the shell, not by reading dates out of the note content). That way, skipping a few nights — laptop off, traveling, whatever — doesn't lose anything; the next run just has a wider window to catch up on. The window resets to zero the moment the timestamp is updated at the end of a run.

## Todo extraction (added)

While consolidating, also pull out any action items from today's meeting notes, daily notes, or other new notes and turn them into Tasks-plugin checkboxes at the source note — not in Todos.md directly:

```
- [ ] <action item> 📅 <due date>
```

Guess a reasonable due date from context (e.g. "by Friday" → next Friday's date) and ask me if it's genuinely unclear. Todos.md queries the whole vault automatically, so nothing needs to be copied there by hand.

## Todo archiving (added)

Also scan the vault for tasks completed more than ~2 weeks ago (checked-off items look like `- [x] ... ✅ YYYY-MM-DD`). For each one found:

1. Append it to `Archives/Todos Archive <year>-<month of completion>.md` (create the month's file if it doesn't exist yet — copy the format from `Archives/Todos Archive Template.md`), including a link back to the note it came from.
2. Remove the checked-off line from the source note once it's archived, so source notes and the dashboard stay lean.

Never archive anything still unchecked, and never touch tasks completed within the last 2 weeks — those stay visible in the "Recently completed" section of Todos.md.

## Knowledge linking (added)

For any note in `Knowledge/` that's new or changed since `last_run`:

1. Read `Knowledge/_Index.md` — one compact table listing every Knowledge note's title, one-line summary, and tags. This is the only full-folder-scale read needed; don't open every file in `Knowledge/` to look for connections.
2. Shortlist candidates from that index by tag/topic overlap with the new note — usually 2-5 notes, rarely more.
3. Open only those shortlisted notes' full text to confirm the connection is actually real, not just a coincidental tag match.
4. Add a link both directions: a "Related" line in the new note pointing to the match, and a link back added into the existing note too.
5. Append one new row to `Knowledge/_Index.md` for the note just processed, so the index stays current without ever being rebuilt from scratch.

Skip this whole section on nights when nothing in `Knowledge/` changed — no index read, no candidate reads, no cost. When something did change, the cost is one index file plus a handful of shortlisted notes, not the whole folder — so it stays roughly flat as `Knowledge/` grows from 10 notes to 500.

## Capture processing (added)

For any file in `Capture/` that isn't already marked `status: processed` (including files with no frontmatter at all — see step 0):

0. First, normalize it against `Capture Template.md`. If it's missing frontmatter fields (`source-type`, `status`, `tags`) or section headers (`Notes`, `AI Notes`), add whatever's missing without touching, reordering, or rewriting any content that's already there. This covers captures that were dropped in without using the template.
1. Read it, and decide where its content actually belongs — a new atomic note in `Knowledge/` (using the same index-shortlist-and-link approach as Knowledge linking above), an addition to an existing People/Projects/Decisions/Companies note, a line in `Ideas to Try.md`, or "not worth keeping." Not everything has to become a Knowledge note; a single capture can be split across several destinations.
2. Act on that decision — move things as you see fit, no approval step. Keep the vault lean: promote only what's genuinely reusable, and let the rest stay preserved in the archived capture rather than manufacturing thin notes. List every disposition in the end-of-run summary so I can review it.
3. Create or update the destination note(s), with a link back to where the capture will end up in `Archives/Capture/`. Update `Knowledge/_Index.md` if a new Knowledge note was created. If the capture's "AI Notes" section carries most or all of the content (little or nothing in "Notes"), add the `ai-sourced` tag before archiving it.
4. Move the original capture file as-is into `Archives/Capture/`, and set its frontmatter to `status: processed` with today's date. Nothing gets deleted, and the raw capture is preserved exactly as written — only its home changes.

5. If the capture being processed cites a raw clip in `Clippings/` (e.g. its "AI Notes" were built from a web clip there), move that clip file into `Archives/Clippings/` now that its content has been consumed. Nothing gets deleted — the clip is preserved, only its home changes. `Clippings/` should be left holding only clips that haven't yet been pulled into a note.

Skip this section entirely on nights when `Capture/` has nothing outstanding — no cost.

## Clippings sweep (added)

Independently of any capture, sweep `Clippings/` for clips whose content has already been fully absorbed into vault notes (a matching Capture is already `processed`, or the material clearly lives in a Knowledge/People/Projects note). Move those into `Archives/Clippings/`. When it's ambiguous whether a clip has been consumed, leave it in `Clippings/` and note it in the run summary rather than archiving it. Skip this section on nights when `Clippings/` is empty or holds only un-consumed clips.

## How to use it

Run this as the last thing you do with your AI assistant each day, pointed at the vault. It turns a day's worth of scattered notes into linked, de-duplicated files, extracts todos with due dates at their source, processes anything sitting in `Capture/`, and surfaces what needs your attention next.

This can also be automated as a scheduled task so it runs every evening without you having to remember to trigger it.
