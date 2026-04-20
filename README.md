# Project Doctrine

> **Use handoff when work needs to continue.
> Use doctrine when judgment needs to continue.**
>
> _Handoff tells an agent what happened.
> Doctrine teaches an agent how to judge._

Most AI agent handoffs tell the next agent *what happened*. Project Doctrine teaches the next agent *how to judge*.

A handoff says:

> We merged PR #42. Next, implement the renderer.

A doctrine says:

> This project separates semantic production from UI rendering. LLMs may propose structure, but deterministic runtime code owns buttons, callbacks, state transitions, and trust boundaries.

That difference matters.

---

## What This Is

Project Doctrine is a method for turning a project's hard-won experience into a reusable posture loader for AI agents.

It captures:

- project ideology
- current state
- validated methods
- operating procedures
- thinking modes
- failure memory
- taste examples
- apprenticeship checks

The goal is not to summarize a project. The goal is to help future agents make better project-native decisions without forcing the user to reteach the same lessons.

---

## Why Handoffs Are Not Enough

Handoffs are useful, but they decay quickly.

They usually answer:

- What happened?
- What changed?
- What should happen next?

They often fail to answer:

- Why was this direction chosen?
- What tempting path should be avoided?
- What kind of output belongs to this project?
- What failures has the project already paid for?
- What should a future agent refuse to do?
- How does a new agent prove it understands the project?

Project Doctrine fills that gap.

---

## Core Idea

Every serious project eventually develops a school.

A school has:

- beliefs
- taboos
- taste
- methods
- scars
- language
- judgment

Project Doctrine makes that school explicit.

---

## The Six-Layer Model

A project doctrine is organized into six layers. See [`docs/six-layer-model.md`](docs/six-layer-model.md) for details.

### L1 — Ideology

What must stay true. The durable beliefs, product philosophy, trust boundaries, and non-negotiables.

### L2 — Knowledge

What is currently true. Current phase, shipped state, active specs, recent commits, open blockers, stale docs.

### L3 — Methods

What has been proven to work. Validated ways of planning, reviewing, implementing, testing, and correcting.

### L4 — SOPs

What should be repeated. Operational recipes for recurring work.

### L5 — Thinking Modes

How to reason. The postures the project needs: evidence-only, dialectic, deterministic, taste review, safety gate.

### L6 — Heart Methods

What the project has paid to learn. Compressed lessons, scars, maxims, and judgment rules with concrete origin.

**L6 is not motivational slogans.** If there is no failure behind it, it probably does not belong in L6.

---

## Doctrine vs Docs vs Memory vs Handoff

| Artifact | Purpose |
|---|---|
| README | Explains what the project is |
| Architecture doc | Explains how the system works |
| Handoff | Explains what just happened |
| Memory | Preserves important facts and preferences |
| **Doctrine** | **Teaches future agents how to judge** |

A good project needs all of them. But they should not be mixed.

See [`docs/doctrine-vs-handoff.md`](docs/doctrine-vs-handoff.md) for the full comparison.

---

## What A Doctrine Skill Looks Like

A typical project doctrine skill looks like this:

```
docs/skills/<project>-session-experience/
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

The most important files are not always the state snapshot.

Often the most valuable files are:

- `failure-memory.md`
- `taste-examples.md`
- `layer-6-heart-methods.md`
- `apprenticeship-check.md`

Those files teach judgment.

---

## Failure Memory

Failure memory records tempting mistakes.

Not blame. Not bugs. Not shame.

A good failure memory entry explains:

- why the wrong move looked reasonable
- how it failed
- how to detect it next time
- what to do instead

Example:

### FM-3: LLM-Generated UI Actions

- **Temptation:** Let the model emit button syntax directly in its response.
- **How it failed:** It blurred the trust boundary between semantic generation and executable UI.
- **Future detection:** Any plan where model output becomes callback data, ids, links, or state transitions.
- **Correct move:** Let the model produce semantic blocks. Let deterministic runtime code render UI.

See [`docs/failure-memory.md`](docs/failure-memory.md) for the full method.

---

## Taste Examples

Taste examples teach what good looks like through contrast.

Adjectives are weak. Examples are stronger.

Instead of saying:

> The product should feel thoughtful.

Show:

**Good:**
The system keeps lifecycle state in the store and renders buttons deterministically.

**Bad:**
The assistant says "I can archive this for you" but no state transition exists.

**Why good wins:**
The first creates recoverable product behavior. The second creates conversational theater.

See [`docs/taste-examples.md`](docs/taste-examples.md) for the full method.

---

## Apprenticeship Check

A new agent should not just read the doctrine. It should prove it can use it.

A good apprenticeship check asks:

- What is current?
- What is durable?
- What is stale?
- Which tempting plan should be rejected?
- Which layer does this task belong to?
- What is the smallest safe next move?

If an agent can answer those, it has entered the project school.

See [`docs/apprenticeship-protocol.md`](docs/apprenticeship-protocol.md).

---

## Quick Start

1. Copy `templates/project-doctrine-skill/` into your project.
2. Fill in `state-snapshot.md`.
3. Write L1, L5, and L6 first.
4. Add at least 3 failure memory entries.
5. Add at least 3 taste examples.
6. Write an apprenticeship check.
7. Use the doctrine before planning new work.

See [`docs/migration-guide.md`](docs/migration-guide.md) for a step-by-step.

## Everyday Use

You don't "manage doctrine" every day. Most of the time you just tell your agent:

> Read the project doctrine first.

Use it at these moments:

- **New session** → read doctrine
- **Big plan** → check doctrine
- **Review direction** → against doctrine
- **Same mistake twice** → into doctrine
- **Big milestone** → update doctrine

Skip it for typos, formatting fixes, and trivial lookups.

Full guide: [`docs/everyday-use.md`](docs/everyday-use.md) / 中文：[`docs/everyday-use.zh.md`](docs/everyday-use.zh.md)

## Maintenance

Do not put everything into doctrine.

> **Git stores history.
> Doctrine stores usable judgment.**

When something important happens, triage it into one of four fates:

- **Keep** — still fires, leave in place
- **Promote** — handoff observation → durable rule (failure-memory, taste, L6)
- **Archive** — historical, mark as such ("Do not use as current doctrine")
- **Delete** — duplicated / misleading / no judgment value (git keeps it if needed)

If unsure, park it in `references/incubation.md` and revisit next review.

Guiding principle:

> **Doctrine should get smaller and sharper over time, not bigger and heavier.**

Full guide (lifecycle, triage template, review cadence, anti-patterns): [`docs/maintenance.md`](docs/maintenance.md) / 中文：[`docs/maintenance.zh.md`](docs/maintenance.zh.md)

---

## Usage Modes

Project Doctrine supports three modes. The six-layer structure is the same; what changes is *where the judgment comes from*.

### Solo Mode

> A doctrine is a memory prosthetic for your future self and your agents.

Building doctrine inside your own project, as you go. Low ceremony. Personal voice OK. Updates without PRs.

Full guide: [`docs/solo-mode.md`](docs/solo-mode.md).

### Team Mode

> A doctrine is a shared judgment contract for humans and agents.

Multiple humans and agents sharing a project. Governance required. Failure memory de-personalized. Two extra files: `governance.md` and `decision-records.md`.

Full guide: [`docs/team-mode.md`](docs/team-mode.md).

### Archaeology Mode

> **Analyze decisions, not personalities.
> Infer norms, not motives.**

Entering a project that already exists — open-source, legacy, inherited, new employer — and inferring its doctrine from public artifacts (PRs, issues, reviews, release notes).

Produces contribution hypotheses, not official rules. Every inferred entry carries confidence + evidence. The goal is reducing review-cycle waste, not gaming maintainers.

Full guide: [`docs/archaeology-mode.md`](docs/archaeology-mode.md) / 中文：[`docs/archaeology-mode.zh.md`](docs/archaeology-mode.zh.md).

### Which mode should I use?

Use **Solo Mode** if you're the primary builder of your own project and work mostly with agents.

Use **Team Mode** if multiple humans + agents contribute to the same codebase and judgment needs to be reviewable.

Use **Archaeology Mode** if you're entering a project from outside and need to understand its public decision patterns before opening PRs.

Use **none** if:
- The project is small and a README is enough
- No real failures or taste decisions have happened yet
- The project is a one-off deliverable with no future audience

**Doctrine is useful after a project has scars — yours, your team's, or the project's you're joining.**

## When Should You Create One?

**Not on day one.**

Create a Project Doctrine after the project has:

- a working skeleton
- a few high-context sessions
- repeated agent mistakes or user corrections
- rejected directions
- meaningful failure memory
- enough taste examples to show what belongs and what does not

Too early, doctrine becomes **aspiration**.
Too late, doctrine becomes **archaeology**.

The best time is: **after skeleton, before sprawl.**

Full guide + readiness rubric + three creation modes (lightweight / full / recovery):
[`docs/when-to-use.md`](docs/when-to-use.md) / 中文：[`docs/when-to-use.zh.md`](docs/when-to-use.zh.md)

---

## Examples

See [`examples/`](examples/):

- [`software-project/`](examples/software-project/) — a fully-fleshed skeleton for a typical software product
- [`trading-agent/`](examples/trading-agent/) — outline for a quant / trading-agent project
- [`ai-short-drama-factory/`](examples/ai-short-drama-factory/) — outline for an AI-content pipeline
- [`research-agent/`](examples/research-agent/) — outline for a long-running research agent
- [`decision-spirit-redacted/`](examples/decision-spirit-redacted/) — pointer to the real-world project this methodology was extracted from

---

## Core Principle

> **Do not summarize the project.
> Extract the school.**

## One-sentence definitions

**Solo Mode:**
> A doctrine is a memory prosthetic for your future self and your agents.

**Team Mode:**
> A doctrine is a shared judgment contract for humans and agents.

**Archaeology Mode:**
> Analyze decisions, not personalities. Infer norms, not motives.

中文：

> 個人模式：Doctrine 是未來的你和你的代理，用來接住現在判斷力的外接記憶。
>
> 團隊模式：Doctrine 是人類與代理共同使用的判斷契約。
>
> 考古模式：分析決策，不分析人格；推論規範，不揣測動機。
>
> **AI 代理越來越會做事，但它們還是不知道一個專案為什麼這樣判斷。
> Handoff 保存工作連續性。
> Project Doctrine 保存判斷連續性。**

---

## License

MIT — see [`LICENSE`](LICENSE).
