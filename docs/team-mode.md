# Team Mode

> **For teams that need shared judgment across humans and AI agents.**
>
> A doctrine is a shared judgment contract for humans and agents.

Team Mode is Solo Mode with governance added. The six-layer model is the same. The difference is in who owns the doctrine, how it changes, and how disputes get resolved.

## When Team Mode fits

Use Team Mode when:

- Multiple humans or agents contribute to the same project
- Onboarding new teammates requires more than reading the README
- Important product judgment lives in 2–3 people's heads
- Reviewers keep explaining the same taste or trust-boundary concerns
- Agents (contractors, AI systems) follow stale plans or generic best practices
- The team has repeated the same architectural mistake more than once

**Team Mode's core question:**

> How do we make our judgment transferable to new humans and new agents without re-teaching the same lessons every month?

## What Team Mode is NOT

Team doctrine is NOT:

- HR policy
- performance review material
- management philosophy
- political alignment doc
- blame log

Team doctrine IS:

> The project's shared judgment system, applied to engineering, product, research, and design decisions.

If a team starts writing doctrine entries about interpersonal conflict, work hours, or accountability, the doctrine is being misused. Those belong elsewhere.

## File structure (team)

Solo mode's 12 files, plus two additions for governance:

```
docs/project-doctrine/                   (or docs/skills/<project>-doctrine/)
  SKILL.md                               (or doctrine-thesis.md — see below)
  state-snapshot.md
  references/  (or layers/)
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
    governance.md                        ← team-only
    decision-records.md                  ← team-only
```

**Directory convention:** either `docs/skills/<project>-doctrine/` (Claude-aware) or `docs/project-doctrine/` (agent-neutral). Pick one per project and stick with it.

**`SKILL.md` vs `doctrine-thesis.md`:** `SKILL.md` is the Claude-skill convention. `doctrine-thesis.md` is a more neutral name that works across agent runtimes. Same content; pick one.

## Governance

### Ownership roles

Teams should define these roles explicitly:

- **Doctrine steward** — owns the overall doctrine's quality; reviews merges; prunes stale entries
- **Product judgment owner** — accepts/rejects changes to L1 product-identity entries and product-related failure memory
- **Engineering judgment owner** — accepts/rejects changes to L1/L3 engineering entries and engineering-related failure memory
- **Review cadence** — how often does the team sweep for stale entries? (weekly, biweekly, post-milestone)

Example `governance.md`:

```markdown
## Doctrine Ownership

- Doctrine steward: @alice
- Product judgment owner: @bob
- Engineering judgment owner: @chen
- Review cadence: every Friday + after major architectural changes
- Conflict resolution: steward mediates; if steward is conflicted, engineering and product owners vote.
```

Without named owners, doctrine becomes a file nobody edits.

### Change process

Doctrine changes go through PRs, reviewed like architecture changes.

Example commit messages:

```
docs(doctrine): add failure memory for generated callback actions
docs(doctrine): update product thesis after surface renderer v0.1
docs(doctrine): mark old agent workflow as superseded
docs(doctrine): add taste example for confirmation-reply copy
```

**PR review questions** (NOT "is the prose good"):

1. Is this entry durable doctrine, or temporary state?
2. Is this team consensus, or one person's preference?
3. Is there concrete evidence behind it (commit, retro, incident)?
4. Does this entry fire for a future agent, or is it too abstract?
5. Does it conflict with an existing L1 / L6 entry?
6. Which layer does it belong in?

### Conflict resolution

When two team members disagree about a doctrine entry:

1. Write both positions in the PR comments
2. Identify whether the disagreement is about **evidence** (fixable by more data) or **value** (requires a decision)
3. For evidence disputes: gather data, reconvene
4. For value disputes: the relevant judgment owner decides; the decision goes in `decision-records.md` regardless of outcome

### Retirement

When an entry becomes obsolete:

- Mark as retired (don't silently delete)
- Include a retirement date and replacement (if any)
- Keep the retired entry searchable — it prevents re-proposing rejected ideas

## Decision records

A team doctrine benefits from lightweight decision records for entries that had contentious history.

Format (minimal ADR-style):

```markdown
## DR-12: Surface Renderer Is Consumer-Only

- **Date:** 2026-04-19
- **Decision:** Surface Renderer is a deterministic view-model consumer. LLM produces semantic blocks; it does not produce buttons, callbacks, or dispatch tokens.
- **Rejected alternative:** Plan C v0.2 — SpiritResponse emits surfaceButtons; renderer parses buttons from response text.
- **Why:** Rejected alternative blurred the trust boundary (see L1.2, FM-1). Producer/consumer split makes prompt regressions independent of UI regressions.
- **Doctrine impact:**
  - Added L1.2 (producer/consumer split)
  - Added FM-1 (LLM-generated UI actions)
  - Plan C v0.2 doc moved to `docs/superpowers/plans/superseded/`.
```

Not every doctrine entry needs a DR — only those where the team considered a specific alternative and chose against it. The DR prevents re-litigation.

## Failure memory in team mode

Team failure-memory is **de-personalized**. No names, no blame, no moral evaluation.

**Good:**

```markdown
## FM-4: Generated Action Boundary Leak

**Temptation:** Let model output include button syntax or callback actions directly.

**How it failed:** Semantic generation and trusted runtime behavior became coupled. Every LLM regression was a UI regression.

**Evidence:** Plan C v0.2 was SUPERSEDED on 2026-02-25 after the producer/consumer boundary was clarified.

**Future detection:** Any design where generated text becomes callback data, ids, links, or state transitions.

**Correct move:** LLM produces semantic blocks. Deterministic runtime renders actions.
```

**Bad:**

```markdown
## FM-4: Bob's Button Plan

Bob wrote a bad plan that let the LLM create buttons, and we had to revert.
```

Team doctrine captures **systemic lessons**, not **personal incidents**.

## Taste examples in team mode

Solo mode lets you say "I don't like this tone." Team mode requires **contrast that any team member can evaluate**.

Every taste entry should be:

- A specific situation
- Two concrete artifacts (good + bad)
- A project-specific reason for "why good wins" that references L1 or L6

If an entry's "why good wins" reduces to "it feels right to me," it isn't ready for team doctrine. Either push harder to extract the principle, or leave it out.

## Apprenticeship check in team mode

Team apprenticeship-check has the same 6 questions as solo, but with one addition:

- Every **new human contributor** answers the 6 questions in their onboarding PR
- Every **new AI agent** (or session) answers them before their first plan
- **Existing contributors** re-run it after significant doctrine changes (not routine state updates)

A failed check from a new contributor often reveals that a layer is under-explained. Treat it as a signal to improve the doctrine.

## When the team grows

Signs the doctrine needs a review:

- New hire struggles with something existing team considers "obvious"
- An AI agent's plan gets rejected for a reason you can't point to in the doctrine
- Multiple reviewers say the same thing independently on different PRs
- A retrospective surfaces a lesson that doesn't already have an entry

Each of these is a doctrine update waiting to happen.

## Anti-patterns in team mode

### Anti-pattern 1: Doctrine becomes company process

If `failure-memory.md` starts containing entries like:

- "PRs must be reviewed within 24 hours"
- "Test coverage must be ≥80%"
- "All code changes go through the CI pipeline"

...the doctrine has drifted into process documentation. Those belong in a separate `docs/engineering-handbook.md` or similar.

Doctrine should answer:

- What judgment does this project need?
- What has it learned not to do?
- What taste defines its output?

Not:

- When do we release?
- Who reviews what?
- What tools do we use?

### Anti-pattern 2: Doctrine becomes founder's book

If every L6 entry is written in one person's voice, and everyone else is just a signatory, the doctrine is a person's memoir, not a team's school.

Fix: require multi-person evidence for new L6 entries. If only one person sees a scar, it may not be team doctrine — it may be personal experience.

### Anti-pattern 3: Doctrine without enforcement

If doctrine exists but PRs don't reference it and plans don't cite it, it's decorative. It must be **consulted** to remain useful.

Fix: make the apprenticeship check part of onboarding. Make "which doctrine entries inform this plan?" a round-2 review question. Make the doctrine load-bearing.

## Solo → Team migration

If your project started solo and is now team-sized:

1. **Re-read existing entries as team.** Which are too personal to survive review?
2. **Depersonalize failure memory.** Rewrite with systemic language.
3. **Appoint owners.** Someone must explicitly own the doctrine.
4. **Add governance.md and decision-records.md.**
5. **Run apprenticeship check with new team members.** Their failures will show which layers are under-populated.
6. **Establish a review cadence.** Weekly sweeps or post-milestone reviews keep the doctrine from calcifying.

## The team-mode self-test

Every month, pick a doctrine entry at random. Ask a team member who didn't write it:

- Does this entry fire for you?
- Would you catch the mistake it describes?
- Does it reflect what the team actually believes?

If the answer is "no," the entry is personal memory, not team doctrine. Either rewrite or retire.

## One-sentence definition

> Team doctrine is the judgment contract between humans and agents that prevents the team from re-paying for already-learned lessons.
