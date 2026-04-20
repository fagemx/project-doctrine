# Doctrine vs Handoff

> Handoff tells an agent what happened.
> Doctrine teaches an agent how to judge.

They are different artifacts. They fail in different ways. They serve different questions. If you conflate them, you get verbose handoffs that still don't help, or doctrines that rot as soon as the state moves.

## The questions each one answers

### A handoff answers:

- What happened in the last session / sprint / week?
- What changed (files, decisions, PRs, state)?
- What is the state of the system right now?
- What should happen next?
- Who is blocked on what?

### A doctrine answers:

- Why was this direction chosen — not once, but as a pattern?
- What tempting path should this project refuse?
- What kind of output belongs in this project?
- What failures has the project paid for, and what do they teach?
- What should a future agent **refuse to do**, even if asked?
- How does a new agent prove it has entered the project's stance?

A capable agent with only a handoff will execute the wrong plan cleanly. A capable agent with only a doctrine will not know where to start. You need both.

## What they look like side by side

### Handoff entry (good)

> **2026-04-20** — Merged PR #128 (citation-in-response feature v0.1). Reports now render source-row citations in every answer. Store-layer idempotency gap flagged in review → follow-up plan written at `docs/plans/2026-04-20-citation-store-idempotency-v0.md`. Next: execute that plan, then manual smoke against the vendor LLM.

Useful. Temporal. Decays in weeks.

### Doctrine entry (good)

> **Producer/consumer split.** LLMs may propose semantic structure (tagged blocks, intents, references). Deterministic runtime code owns button rendering, callback routing, state transitions, and trust boundaries. We paid for this with v0.2 (SUPERSEDED): the model was allowed to emit dispatch-critical tokens directly in its response text. It blurred responsibility and made every LLM regression into a UI regression. Never again put dispatch-critical tokens in generated text.

Durable. Explains why a whole class of future temptations will be refused.

## Failure modes

### Handoff failure: "true but useless"

```
Merged PR #128. Next: idempotency plan.
```

Technically accurate. A fresh agent reading this has no way to know:
- Why idempotency matters here
- What the trust model is
- Whether the next plan should be small (it should) or big (a previous team member might assume big)

### Doctrine failure: "stale beliefs"

```
"Central memory layer pending" — we're building a collaborative memory surface.
```

This was true three months ago. Now it's replaced by a newer architectural framing. An agent loading this doctrine will plan toward a frame that no longer exists.

**Handoff fails when too thin. Doctrine fails when not refreshed.**

## When to reach for each

| Situation | Use |
|---|---|
| Starting a new session on familiar project | Handoff first (state), then doctrine (judgment) |
| New agent / new team member onboarding | Doctrine first, then current handoff |
| "Why are we doing it this way?" | Doctrine |
| "What's the next task?" | Handoff |
| "Should I add feature X?" | Doctrine (is it in the school?) + handoff (is now the time?) |
| "How should I test this?" | Doctrine (L3 methods) |
| "Which files changed last week?" | Git log, not either of these |

## The decay curve

- **Handoff** decays fast. A three-month-old handoff is usually misleading. Treat anything > 2 weeks as archaeology.
- **Doctrine L2 (knowledge)** decays. Treat as a dated snapshot; refresh weekly or on state change.
- **Doctrine L1 (ideology)** is supposed to NOT decay. If it changes, the project has shifted identity — flag it loudly.
- **Doctrine L3–L6** (methods / SOPs / thinking modes / heart methods) should grow, not churn. Entries should be added when validated and removed only when proven wrong.

## Where doctrine ends and memory begins

**Memory** (user memory, Claude auto-memory, etc) holds facts: "user prefers squash merges", "this repo uses vitest", "the chat bot's handle is X". Stateful, specific, often personal.

**Doctrine** holds stance: "we separate semantic production from rendering", "we refuse LLM-generated UI actions", "we test with real LLMs not mocks". Collective, reusable, carries *why*.

A good memory entry can graduate to doctrine when it stops being personal preference and starts being project law. A good doctrine entry can demote to memory when it becomes a universal convention not specific to the school anymore.

## Mental model

Think of a handoff as a **baton**. It's passed. The last runner's progress matters; their running style doesn't.

Think of a doctrine as a **dojo**. Everyone who trains here carries the stance, regardless of who else is in the room today.

An agent that inherits the baton but not the dojo runs fast in the wrong direction.

## Summary

- Handoff = "here is where we are" — narrative continuity
- Doctrine = "here is how we judge" — judgment continuity
- They are complements, not substitutes
- Keep them in separate files with separate decay rules
