---
name: project-doctrine-builder
description: Teaches you how to build a Project Doctrine skill for a given project. Use when a project has accumulated enough judgment that handoffs are no longer sufficient and a 6-layer doctrine is the right response.
---

# Project Doctrine Builder

This skill teaches how to build a Project Doctrine skill for your project. It is a **meta-skill**: it doesn't load a specific project's posture — it guides you through creating one.

**Announce at start:** "I'm using the project-doctrine-builder skill to design the doctrine for <project>."

## When to use

Use this skill when:

- A project has been running ≥ 1 month with real failures
- Multiple agents or sessions work on the project
- You've caught yourself re-explaining the same convictions to fresh sessions
- A handoff doesn't carry enough context to let a new agent judge well
- The user is asking "how do I preserve what we've learned here?"

Do NOT use this skill for:

- Day-1 projects (you haven't paid for enough lessons yet)
- Projects with no recurring agent work
- One-off tasks (doctrine has no future audience)
- Projects where a README or CLAUDE.md is sufficient

## First ask: Solo or Team mode?

Before building anything, clarify:

- **Solo Mode** — one primary builder + one or more AI agents. Low ceremony. Personal voice OK. Updates without PRs.
- **Team Mode** — multiple human contributors (plus agents). Governance required. Failure memory de-personalized. Two extra files: `governance.md` and `decision-records.md`.

The structure is the same; the discipline is different. See `docs/solo-mode.md` and `docs/team-mode.md` in the project-doctrine repo for detail.

If unclear, ask: "Will more than one human contribute to this doctrine, or is it just you + agents?"

## What you produce

By the end of using this skill, you should have:

```
docs/skills/<project>-doctrine/   (or .claude/skills/<project>-doctrine/)
  SKILL.md
  references/
    state-snapshot.md
    layer-1-ideology.md
    layer-2-knowledge.md
    layer-3-methods.md
    layer-4-sops.md
    layer-5-thinking-modes.md
    layer-6-heart-methods.md
    failure-memory.md
    taste-examples.md
    apprenticeship-check.md
    bootstrap-prompt.md
    provenance.md
```

Not all files need to be fully populated on v0 — see `references/templates.md` for per-file minimum viable content.

## References

- [`references/doctrine-model.md`](references/doctrine-model.md) — the conceptual model (what doctrine is, what it isn't)
- [`references/layer-guide.md`](references/layer-guide.md) — per-layer "what belongs here, what doesn't"
- [`references/failure-memory-guide.md`](references/failure-memory-guide.md) — how to write failure-memory entries
- [`references/taste-examples-guide.md`](references/taste-examples-guide.md) — how to write taste-example entries
- [`references/apprenticeship-protocol.md`](references/apprenticeship-protocol.md) — the 6-question check
- [`references/templates.md`](references/templates.md) — the full template set for copy-paste

## The bootstrap process (v0)

Order matters. Don't try to write all 12 files at once.

1. **Observe.** Spend 15 minutes reviewing the user's current project. Read recent PRs, CLAUDE.md, any retros. Notice what the user explains twice in conversation.
2. **Write state-snapshot first.** The volatile layer is the easiest to write and the highest-value to externalize.
3. **Write L1 next.** 3–5 durable convictions. Each with a violation test.
4. **Write L6 next (if scars exist).** One entry per real scar. If there are no scars, note that L6 is empty for now.
5. **Write 3 failure-memory entries.** Pick the most-repeated tempting mistakes.
6. **Write 3 taste examples.** The most recent "no, not like that — like this" moments.
7. **Write L2 as an index.** Point at authoritative docs; don't duplicate them.
8. **Write L5 (thinking modes).** 2–4 stable reasoning postures.
9. **Write the apprenticeship check.** 6 questions, customized.
10. **Write the bootstrap prompt.** Copy-paste loader for fresh sessions.
11. **L3 and L4 can start empty or minimal.** Populate as methods validate and SOPs recur.

## Critical rules

- **No scar, no L6.** If a proposed L6 entry has no concrete failure origin, reject it.
- **L3 requires validation.** Methods go in L3 only after they've worked in your project.
- **State-snapshot is dated.** Undated snapshots rot silently.
- **L1 is conservative.** If you're adding L1 entries weekly, most aren't actually durable.
- **Taste examples are contrast pairs.** A single "this is good" isn't a taste example.
- **Do NOT let the user treat the doctrine as lore.** It's a working document. It changes as the project changes.

## Voice

- Short sentences
- Declarative, not exploratory
- Bilingual is fine if the project is bilingual
- No motivational slogans
- Examples > adjectives
- Each entry should be readable in under a minute

## How to run this skill

When the user asks you to apply this skill:

1. Announce ("I'm using the project-doctrine-builder skill...")
2. Confirm the project is ready (see "When to use" above)
3. Walk through the 11 bootstrap steps
4. For each step, generate the content AND explain why it belongs there
5. Write the files as you go
6. At the end, run the apprenticeship check against the fresh doctrine to test it

## Completion criterion

The doctrine is v0-done when:

- [ ] state-snapshot.md is dated and current
- [ ] layer-1-ideology.md has ≥3 entries with violation tests
- [ ] layer-5-thinking-modes.md has ≥2 entries
- [ ] layer-6-heart-methods.md has ≥1 entry with a scar (or is explicitly empty with a note)
- [ ] failure-memory.md has ≥3 entries
- [ ] taste-examples.md has ≥3 contrast pairs
- [ ] apprenticeship-check.md has 6 customized questions
- [ ] bootstrap-prompt.md has a copy-paste loader
- [ ] A fresh agent can answer Q1–Q6 of the apprenticeship check project-specifically

After v0, the doctrine grows with the project. Weekly maintenance beats occasional rewrites.

## One-sentence principle

> **Do not summarize the project. Extract the school.**
