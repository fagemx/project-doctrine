# The Six-Layer Model

A project doctrine is organized into six layers. Each layer solves a distinct problem. A reader who understands one layer often over- or under-fills the others. This doc is the reference for which content belongs where.

```
┌─────────────────────────────────────────────────────────┐
│ state-snapshot        — volatile: current state         │
├─────────────────────────────────────────────────────────┤
│ L1 Ideology           — WHY (durable convictions)       │
│ L2 Knowledge          — WHERE (pointers to source docs) │
│ L3 Methods            — HOW (validated approaches)      │
│ L4 SOPs               — WHAT TO REPEAT (procedures)     │
│ L5 Thinking Modes     — HOW TO REASON (metacognition)   │
│ L6 Heart Methods      — COMPRESSED REFLEX (scars)       │
└─────────────────────────────────────────────────────────┘
```

Layers 1, 3, 5, 6 are *stable*. Layer 2 is *moderately stable*. Layer 4 grows situationally. State-snapshot is *volatile* and sits above the layers.

---

## L1 — Ideology

**Question:** *What must stay true about this project?*

**Contains:**
- Product identity — what the thing is, what it is not
- Trust boundaries — who/what is allowed to decide what
- Non-negotiables — things that will not be traded
- Durable convictions — beliefs that predate the current code

**Criteria:**
- If you removed it, the project would not be the same project
- It was true three months ago AND is expected to be true three months from now
- Violating it would be a category error, not a mistake of degree

**Examples (software-product):**
- "We separate semantic production from UI rendering. LLMs propose structure; deterministic code owns dispatch."
- "Reliability outranks feature velocity. A shipped regression loses more trust than an unshipped feature loses excitement."
- "User actions must be recoverable. No action is complete until it leaves a visible audit trail."

**Anti-examples (don't put these in L1):**
- "We use TypeScript strict mode." → This is L3 (method) or L4 (SOP), not conviction.
- "We ship on Thursdays." → This is L4 (SOP) and also volatile; it belongs in state-snapshot if current.
- "The team agrees async is better than sync." → Probably L5 (thinking mode) or L6 (heart method with a scar behind it). Too operational for L1.

**Volatility:** Very low. If L1 changes, announce it loudly.

---

## L2 — Knowledge

**Question:** *Where is the current truth written?*

**Contains:**
- A pointer list to authoritative specs / architecture docs
- A reading order (what to read first, what to read only on demand)
- Named concepts defined once and pointed at everywhere else
- "What to forget" — docs that used to be canonical and are now superseded

**Criteria:**
- Content lives in the referenced doc, not in L2. L2 is an index.
- Every entry has a last-verified date or a commit pointer.
- If a referenced doc is retired, L2 marks it as retired (don't silently delete).

**Examples:**
- "Architecture: see `docs/specs/2026-04-11-shared-artifact-architecture-note-v0.md` (canonical)."
- "Reading ladder for a new session: state-snapshot → shared-artifact note → product-definition v2.1."
- "Superseded: `2026-04-01-cognitive-router-v0.md` (replaced by `v0.2` on 2026-04-15)."

**Anti-examples:**
- Full explanations of what a spec says. → Put those in the spec, not in L2. L2 is a map.
- "We use React." → L3/L4, not L2.
- Facts about the user. → Memory, not doctrine.

**Volatility:** Moderate. Refresh when specs move. Don't let it grow into a duplicate of the specs themselves.

---

## L3 — Methods

**Question:** *How do we actually do the work — methods that have been tested?*

**Contains:**
- Planning methods (writing-plans, round-2 review, etc.)
- Implementation methods (TDD shape, subagent-driven execution, etc.)
- Review methods (pr-review-loop, scope-fence checks)
- Testing methods (real-LLM smoke vs unit, integration-first)
- Debugging methods (bisect, binary search, minimal repro)

**Criteria:**
- **You have used this method and it worked.** Un-tested methods go in an "experiments" file, not L3.
- It's reusable — more than one situation benefits from it.
- It has at least one concrete example from your project.

**Examples:**
- "TDD per task: write failing test → verify it fails → implement minimum → verify pass → commit. Proven on the v0.1 adapter fix where the trailing-row bug was caught by the test before it shipped."
- "Round-2 review before execution. Plan writer produces v1; reviewer surfaces blockers; plan patches in place; only then execute. Used across our last 5 sequential plans — every one caught ≥3 blockers."
- "Scope-fence check before every PR: `git diff main -- <forbidden-paths>` must be empty."

**Anti-examples:**
- "We should use feature flags." → Aspirational; if not yet validated in your project, not L3 yet.
- Generic "best practices" from blog posts. → If it hasn't been pressure-tested in your project, it doesn't belong.

**Volatility:** Low, but additive. Add methods as you validate them.

---

## L4 — SOPs

**Question:** *What procedure do we run when situation X happens?*

**Contains:**
- Concrete step-by-step recipes for recurring situations
- Each SOP named by the situation that triggers it, not by the tool used
- Entry conditions, steps, exit conditions

**Criteria:**
- Triggered by a specific situation you see often
- Has a defined exit ("done means X")
- Used more than once — one-off procedures don't need SOPs

**Examples:**
- "**SOP-1: New directive arrives.** (1) Decompose the directive. (2) Produce 2–3 approach options. (3) Ask clarifying question if range unclear. (4) Wait for green light. (5) Execute."
- "**SOP-3: Regression in a test suite.** (1) Classify the failure type: dilution / capacity / conflict / flake. (2) Do NOT add new rules first. (3) Reproduce minimally. (4) Check the single-variable change that introduced it. (5) Fix at root cause."

**Anti-examples:**
- "How to use git." → Not a project-specific procedure.
- "How to think about architecture." → L5 (thinking mode), not procedural.

**Volatility:** Grows situationally. You add an SOP when a situation recurs for the third time.

---

## L5 — Thinking Modes

**Question:** *What reasoning posture does this project need me to adopt in real time?*

**Contains:**
- Metacognitive checks ("am I drifting into listing?")
- Posture switches ("this is a taste question, not an engineering question — slow down")
- Self-observation rules ("if I'm defending instead of examining, stop")

**Criteria:**
- It's about *how* you're thinking, not *what* you're thinking
- It's something a capable agent *could* do but often forgets
- It's useful every session, not just in one situation

**Examples:**
- "**Observe your own drift.** Signals: you're listing instead of judging; you're adding rules instead of understanding the failure; you're defending a decision instead of examining it. When you notice, stop."
- "**Surface uncertainty explicitly.** When the right answer is not obvious, say so out loud. Guessing fluently is worse than saying 'I don't know, let me check X.'"
- "**Hunt counter-examples before confirming.** If you have a thesis, spend 30 seconds looking for the thing that would invalidate it."

**Anti-examples:**
- "Use TDD." → That's L3.
- "Don't use any." → That's a rule, not a thinking mode.

**Volatility:** Very low. These are stable reasoning postures.

---

## L6 — Heart Methods

**Question:** *What has this project paid to learn — in compressed, memorable form?*

**Contains:**
- Short maxims (one sentence, sometimes bilingual)
- Each one tied to a concrete failure or a concrete hard-won success
- Reflex-level compression — you should be able to recite it mid-task

**Criteria:**
- **There is a scar behind it.** No failure, no L6.
- It compresses a lesson the project has already paid for
- It's short enough to hold in working memory
- It triggers the right question, not the answer

**Examples:**
- "**Framing > model capacity.** Scar: spent a week tuning the main LLM prompts before realizing the framing itself was wrong."
- "**減法比加法難.** Subtracting rules is harder than adding them — prompts are zero-sum, every addition dilutes something."
- "**Hard ban is discipline, not reminder.** A 'never do X' rule requires treating X as inadmissible, not as something to remember to skip."

**Anti-examples:**
- "Move fast and break things." → No specific scar; generic slogan.
- "Be kind in code reviews." → Noble, but it's a value, not a compressed lesson with a specific failure origin.
- A technical rule: "Always validate at system boundaries." → That's L3 (method) unless you have a specific failure that makes it a scar.

**Volatility:** Only grows. Entries are added when you recognize a scar has been earned. Entries are retired only if the lesson turns out to be wrong.

---

## The state-snapshot (not a layer)

**Question:** *Where are we right now?*

Lives above the layers. Volatile by design. Contains:

- Current phase / frontier of work
- What's shipped vs what's staging
- Active specs, current PR list, open blockers
- What to ignore (old assumptions that are no longer true)
- A dated "last reviewed" header

**Criterion:** If it's not true this week, update it this week.

---

## Decision rubric: which layer does this go in?

Ask in order:

1. **Is it about current state?** → state-snapshot
2. **Is it a durable belief that defines the project?** → L1
3. **Is it a pointer to a longer doc?** → L2
4. **Is it a way of doing work you've validated?** → L3
5. **Does it have a defined trigger and steps?** → L4
6. **Is it about how to think / observe yourself while working?** → L5
7. **Is it a compressed lesson with a concrete scar?** → L6
8. **None of the above?** → It's probably not doctrine. Consider: is it memory? Is it architecture? Is it just a note?

If it could live in two layers, ask: *when does a reader need this?* L1 is loaded every session. L2 is loaded on demand. L3 comes up during planning. L4 during execution. L5 continuously. L6 as mid-task triggers. Place it where the reader most needs it.

## Common misplacements

- **Aspirational methods in L3.** If you haven't used it, it's not validated. Don't graduate it.
- **Generic slogans in L6.** If there's no scar, it's not heart method. Demote to L1 or delete.
- **Full spec content in L2.** L2 is an index, not a mirror. Point, don't copy.
- **State-of-the-world in L1.** "We're currently building X" goes in state-snapshot, not L1. L1 is "what we always build toward."
- **User preferences in L1.** User preferences go in memory. L1 is collective project stance.

## What a healthy doctrine looks like

- L1 short (< 10 items), stable, rarely changes
- L2 is an index, stays thin, refreshed with each major architecture move
- L3 grows slowly (one validated method at a time)
- L4 grows situationally, sometimes pruned when situations stop recurring
- L5 is very stable, one or two additions per year
- L6 accrues like sediment — one entry per real scar
- state-snapshot changes weekly or more

If L3 is enormous and L6 is empty, the project is generating methods without accumulating scars — likely over-prescribing and under-learning.

If L6 is enormous and L1 is empty, the project knows what to avoid but not what it's for.

A healthy doctrine has all six layers populated, and each is small enough to carry in one read.
