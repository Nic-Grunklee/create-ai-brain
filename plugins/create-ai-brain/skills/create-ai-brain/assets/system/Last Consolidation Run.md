---
type: system
tags: [system, todos]
last_run: 1970-01-01T00:00:00Z
---

# Last Consolidation Run

Tracks when the nightly consolidation prompt last ran, so the next run knows how far back to look — instead of assuming "today," which breaks if you skip a night (or several).

Don't edit `last_run` by hand. The consolidation prompt updates it automatically at the end of every run.

(The initial timestamp is set to the epoch so the very first consolidation run treats every existing file as new and catches up on the whole vault. After that first run it self-maintains.)
