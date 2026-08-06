---
type: prompt
tags: [prompt, books, system]
---

# Book Processing Prompt

Run this on-demand, once you've actually finished a book — not nightly, not automatic. Point it at the specific book note in `Books/`.

```
Read <book note> in Books/. First, research the book and add a concise "AI Notes" section to the file:
- A short synopsis for context.
- Actionable takeaways and frameworks written with future blog posts in mind — push past the obvious, dust-jacket version of each idea to what's actually specific, arguable, or non-obvious about it. Real opinions and angles, not generic summary bullets restating the book's marketing copy.
Keep this clearly separate from my own Notes and My Takeaways sections — don't rewrite or absorb them.
Then, using my raw Notes, My Takeaways, and the new AI Notes section together, shortlist which ideas are genuinely reusable enough to become their own atomic note in Knowledge/ — not everything, just the ones with legs outside this one book. Show me the shortlist before creating anything.
Finally, draft 2-3 potential blog post angles from the actionable takeaways — a hook/title and a one-line pitch each — into the "For future writing" section of the book note.
```

## How to use it

1. Claude adds an "AI Notes" section to the book file first — a short synopsis plus actionable takeaways written with an eye toward future blog posts, not a generic dust-jacket summary. Each takeaway should have a real angle or opinion, not just restate the book's stated themes. It stays in its own section, never merged into "Notes" or "My Takeaways," so your own material is never touched.
2. Claude then shortlists Knowledge candidates using all three of your/its sections together — Notes, My Takeaways, and whatever AI Notes surfaced. Review the shortlist. You decide what actually becomes a permanent note — same rule as everywhere else in this vault: the AI surfaces candidates, you curate.
3. For each one you approve, Claude creates the atomic note in `Knowledge/` (with a `Source` line linking back to this book note), appends a row to `Knowledge/_Index.md`, and adds a link to it under "Derived notes" in the book note.
4. The raw book note itself never gets deleted or moved — it stays in `Books/` permanently as the full source record. Only the ideas you approve get promoted out into `Knowledge/`.
5. Claude also drafts a few potential blog post angles — a hook/title plus a one-line pitch each — straight into "For future writing," pulled from the actionable takeaways. This is starting material to react to, not a finished draft; develop whichever one actually grabs you, ignore the rest.

## Writing about books later

"For future writing" gets seeded automatically during processing, but it's not locked to that moment — when you're actually ready to write, ask directly (e.g. "help me develop this angle further" or "give me new angles now that I've had time to sit with the book") and have Claude add or revise material there. Keeping it in its own section means it's always clear what's your original capture versus AI-assisted synthesis.
