# Identity Interview — building IDENTITY.md, USER.md, SOUL.md

The three identity files are what make the vault *personal*. Every agent session in the vault reads them first (via `CLAUDE.md` / `AGENTS.md`), so getting them right is what turns a generic assistant into one that already knows how the owner works and talks the way they want.

The origin prompt (from Dan Martell's "This AI Brain Will Make You So Smart It's Almost Unfair") is:

> Interview me about how I work, what I value, how I communicate, and what I want from an AI assistant. Then draft my USER, SOUL, and IDENTITY files.

This skill runs that interview live rather than dumping a blank questionnaire. Conduct it as a real conversation: ask a few questions at a time, follow up on anything thin or generic, and keep going until you have concrete, specific material — not platitudes. Then draft all three files and let the owner edit.

## What each file is for

- **IDENTITY.md** — the facts. Name, current role, where they're headed, where they do their best work, and what this vault is to them. Short.
- **USER.md** — the operating manual. How they work day-to-day, what they're currently focused on, and what "good" looks like from an assistant. Concrete and current — this is the file most likely to change over time.
- **SOUL.md** — the values and voice. What they care about, and exactly how the assistant should talk to them (tone, directness, what to avoid). This is what shapes every reply's *style*.

## Interview questions

Work through these in conversation. Don't just read them off — dig where answers are vague. Group them so you're not firing all of them at once.

### Identity (→ IDENTITY.md)
1. What's your name, and what should the assistant call you?
2. What's your current role or main line of work?
3. Where are you headed — the role, level, or kind of work you're moving toward?
4. Where do you do your best work? What kind of problem or setting brings out your strongest thinking?
5. What is this vault to you right now — a mission-critical system, or an experiment you're feeling out?

### Work style (→ USER.md)
6. Walk me through how you actually work. Solo and heads-down, or visible and collaborative? Planner or prototyper?
7. What are you focused on right now — the initiatives or habits you're actively trying to build or improve?
8. What kinds of people or environments do you do your best work around?
9. Whose thinking, systems, or content has shaped how you want to work? (Books, people, frameworks.)
10. When an assistant is genuinely useful to you, what did it just do? Give a concrete example of "good."
11. What do you want the assistant to stop doing, or never do?

### Values and voice (→ SOUL.md)
12. What do you value most in how work gets done — the things you won't compromise on?
13. How do you want the assistant to talk to you? Direct and blunt, or warm and encouraging? Long or terse?
14. Do you want it to push back and disagree with you, or mostly execute? If push back — how should it back that up (framework, data, just say it)?
15. What tone or habits instantly annoy you? (Fluff, hedging, over-apologizing, emoji, exclamation points, small talk...)
16. When you're unsure or the situation is ambiguous, should the assistant ask first or make a reasonable call and tell you after?

## Drafting the files

After the interview, draft all three using the formats below. Keep them tight — these get read at the start of every session, so every line should earn its place. Write SOUL.md's "Communication style" and "Behavioral defaults" as literal instructions to the assistant, because that's exactly how they'll be used. Show the drafts, invite edits, and only then write them into the vault root.

### IDENTITY.md format
```markdown
---
type: identity
tags: [system, identity]
---

# IDENTITY

**Name:** <name>

**Current role:** <role>

**Where I'm headed:** <trajectory>

**Where I operate best:** <the kind of problem/setting where they do their best work>

**What this vault is:** <one or two lines on what the vault is to them right now>
```

### USER.md format
```markdown
---
type: user
tags: [system, user]
---

# USER

## Work style

- <bullets: how they work, collaboration style, planner vs prototyper, influences>

## Current initiatives

- <bullets: what they're actively building/improving right now>

## What "good" looks like from an assistant

- <bullets: concrete descriptions of useful assistant behavior, drawn from their examples>
```

### SOUL.md format
```markdown
---
type: soul
tags: [system, soul]
---

# SOUL

## Values

- <bullets: what they care about / won't compromise on>

## Communication style (how the assistant should talk to me)

- <bullets: literal instructions — tone, directness, length, what to avoid>

## Behavioral defaults

- <bullets: default behaviors — e.g. when to ask vs. act, turn action items into todos, extract meetings a certain way>
```

## Keeping them alive

These aren't write-once. As the owner's role, focus, or preferences shift, they should update USER.md especially. A good habit: whenever the assistant clearly missed on tone or priorities, ask "should I update SOUL.md / USER.md so this sticks?" and fold the correction in.
