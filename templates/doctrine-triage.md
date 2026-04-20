# Doctrine Triage

> Copy this template per candidate. Fill in → decide → route to the right layer OR archive OR delete OR leave in incubation.

Use when something doctrine-shaped just surfaced and you're not sure what to do with it.

---

## Candidate

<Short name — one phrase that a future reader would recognize. e.g. "Generated callback actions coupling producer and consumer">

## Source

<Where did this come from? Be specific.>

- [ ] Long session transcript (link or date)
- [ ] PR / revert
- [ ] Postmortem
- [ ] User correction
- [ ] Plan round-2 review
- [ ] Experiment result
- [ ] Other: ___

## What happened (facts)

<2–5 bullets describing the concrete event or observation. No interpretation yet.>

-
-
-

## Why it may matter

<One sentence. If you can't write one, it probably doesn't matter enough for doctrine.>

## Has this pattern appeared before?

- [ ] Yes — <when / where>
- [ ] No, but the cost is high enough that once is enough
- [ ] Not sure — incubate

## Classification

Pick ONE primary bucket. (Something can touch multiple, but pick the primary.)

- [ ] **State snapshot** — current state that a fresh agent needs to orient
- [ ] **Failure memory** — tempting-but-wrong pattern, four-field entry
- [ ] **Taste example** — concrete good/bad contrast, project-specific why
- [ ] **L1 ideology** — durable conviction with a violation test
- [ ] **L3 method** — validated way of working with a concrete example
- [ ] **L5 thinking mode** — real-time reasoning posture
- [ ] **L6 heart method** — compressed lesson with a concrete scar
- [ ] **Archive** — historically important, not current, needs "historical" marker
- [ ] **Delete** — no judgment value, git already holds it if needed
- [ ] **Incubate** — not sure yet, park in `references/incubation.md`

## Layer-of-origin questions (pick only the relevant set)

### If Failure memory:
- **Temptation (agent-voice):**
- **How it failed (concrete symptoms):**
- **Future detection (pattern match):**
- **Correct move (doable substitute):**

### If Taste example:
- **Situation:**
- **Good (concrete artifact):**
- **Bad (concrete artifact, seductively plausible):**
- **Why good wins (project-specific, references L1 or L6):**

### If L6 heart method:
- **Maxim (one line):**
- **Scar (the specific failure that earned this):**
- **Triggers when (the situation where this fires):**

### If L1 ideology:
- **Claim:**
- **Why (justification, what we paid):**
- **Violation test:**

## Decision

<Promote to [X], or archive, or delete, or incubate. One sentence with reasoning.>

## Review date

<If incubated: when do we revisit? Date OR trigger (e.g. "after next milestone").>

## Author / session

<Who / what session wrote this triage.>

---

## Notes for the maintainer

- **If the "why it may matter" field is vague, lean toward incubate.** Force yourself to write it concretely first.
- **If a Failure memory entry's detection heuristic is generic ("be careful with X"), it's not ready.** Sharpen or incubate.
- **If L6 has no scar, reject.** No scar, no L6.
- **Archive needs a "historical" marker in the destination file.** Don't forget.
- **Delete means delete.** Git keeps the history. The doctrine layer doesn't need it.
- **If you find yourself choosing "Incubate" every time, you're probably too cautious.** The incubation pile itself decays — after a month unmoved, delete it.
