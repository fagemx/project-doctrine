# Failure Memory

> Most teams document what they built. Few document what they refused to build, and why.

Failure memory is the doctrine file that usually matters most. It captures the tempting-but-wrong paths your project has seen, the failures they caused, and the detection heuristics that catch them early next time.

It is not a bug tracker. It is not a post-mortem archive. It is a **trap map**.

## What a failure memory entry is

A useful entry has four fields:

1. **Temptation** — what would a reasonable agent/engineer plausibly try?
2. **How it failed** — what went wrong, concretely?
3. **Future detection** — what early signal should a future agent watch for?
4. **Correct move** — what should happen instead?

If any of those four fields is vague, the entry isn't useful yet.

## What it is NOT

- **Not a bug list.** A bug fix is a handoff item. Failure memory generalizes from the bug to the *class* of tempting mistake.
- **Not shame.** Entries are about moves that looked reasonable at the time. If the failure was obvious negligence, you probably don't need an entry — you need a process fix.
- **Not exhaustive.** Failure memory is lossy compression: dozens of near-misses distilled into a few durable traps.

## Example entry

```markdown
## FM-3: LLM-Generated UI Actions

**Temptation:**
Let the model emit button syntax or callback data directly in its response —
it's "all just text" and the framework renders it, so why add a layer?

**How it failed:**
- LLM hallucinated button labels that didn't map to any handler
- Prompt regressions became UI regressions (no separation of concerns)
- Callback data parsing needed quoting escapes that LLMs got wrong ~5% of the time
- User-visible "button ghosting": buttons appeared but did nothing

**Future detection:**
Any plan where:
- Model output becomes callback data
- Model output becomes URL path, link, or ID
- A regex in production parses model output to route
- The phrase "the assistant will output" appears near a dispatch path

**Correct move:**
LLM produces semantic structure (`blocks`, `tags`, `intents`). A deterministic
renderer maps that structure to platform primitives. Trust boundary is explicit:
model owns meaning, code owns dispatch.
```

That entry is doing four jobs:
- Teaches a *class* of mistake (not one bug)
- Gives a future agent early-warning heuristics
- Names the correct alternative
- Makes the trust-boundary principle concrete

## Why this format works

- **Temptation** is written from the POV of the agent who would make the mistake. This is crucial: if a future agent doesn't recognize themselves in the "temptation" field, the entry won't fire.
- **How it failed** with concrete symptoms, not abstractions. "It was messy" doesn't help; "prompt regressions became UI regressions" does.
- **Future detection** is a *pattern match*, not a checklist. It should be short enough to remember and specific enough to fire.
- **Correct move** is the minimum-viable alternative. Not "rebuild everything"; the actual doable substitute.

## How many entries

A healthy failure-memory file has between 5 and 25 entries. Fewer than 5 — you haven't accumulated enough experience to have doctrine-worthy entries (or you have, but you haven't written them). More than 25 — you've stopped compressing and started logging; consider consolidating.

New entries go at the top. Retire entries that turn out to be wrong (don't silently delete — mark as retired with a note).

## When to add an entry

Add one when:

- A round-2 review catches a class of mistake, not just a typo
- You say "we already tried this" in conversation for the second time
- The user corrects the same pattern twice
- An experiment produces a clear "don't go this way" result worth carrying forward
- A PR is rejected for a reason that will apply to future PRs

## When NOT to add an entry

Skip the entry if:

- The failure was a single-instance bug, not a pattern
- The lesson is covered by an existing entry (extend or consolidate instead)
- The "correct move" is just "write more tests" or "be more careful" (those are not moves)

## Where it lives

In the doctrine skill's `references/failure-memory.md`. Referenced from:

- L2 knowledge (as a pointer)
- L6 heart methods (individual entries may compress into a maxim)
- Apprenticeship check (new agents should be able to name 1–2 traps)

## Tone

Direct. Technical. No hedging. "This looked reasonable. It failed. Here's the shape." A failure memory written with corporate euphemism doesn't fire in an agent's attention.

## Anti-patterns in failure memory

- **Vague temptation:** "might be tempted to over-engineer" → not a trap, just a virtue
- **Moralistic correct move:** "should have thought more carefully" → not actionable
- **No detection heuristic:** entry describes failure but gives no way to see it coming
- **Entries that re-litigate the bug:** if a reader can't tell what to do differently next time, the entry is a bug report in disguise

## The self-test

After writing an entry, ask a fresh agent (or yourself with a day of distance):

> "Here's a plan. Does this trigger any failure-memory entry?"

If the agent can't answer from the entries alone, the entries aren't doing their job.

---

## Starter entries most projects need

These are not universal, but they show up in most software projects that work with LLMs:

- **LLM-generated dispatch tokens** (as above)
- **Mocking what should be integration-tested** (the fix passes, prod breaks)
- **Adding a rule to the prompt instead of reframing**
- **Optimizing a model for a benchmark that doesn't reflect user experience**
- **Turning a scope-fence into a guideline instead of a hard invariant**
- **Assuming the model "understands" a constraint it was merely told**

If you're starting a failure-memory file from scratch and those patterns have bitten your project, that's where to begin.
