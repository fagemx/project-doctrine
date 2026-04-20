# Apprenticeship Check — Acme SaaS

A new agent (or a fresh session) answers these six questions before taking on real work.

## Q1 — What is current?

Name 2–3 things true about Acme SaaS right now, drawn from `state-snapshot.md`.

## Q2 — What is durable?

Name 1–2 L1 convictions that would constrain any new plan.

## Q3 — What is stale?

Name one doctrine entry or referenced doc that is no longer accurate. Explain.

## Q4 — Which tempting plan should Acme refuse?

From `failure-memory.md`, name one trap and describe a situation where it would fire.

## Q5 — Which layer does [task X] belong in?

Given a task the user provides, place it in the right layer.

## Q6 — What is the smallest safe next move?

Given the current state, propose one minimum-viable next action. Justify against L1.

---

## Sample good answer

> **Q1:** Citation-in-response shipped 2026-04-15. We're in trust-hardening phase — no new AI features until citation coverage ≥95%. On-call runbook for AI outages is in progress.
>
> **Q2:** L1.1 (trust > speed) and L1.3 (every AI answer must be citable). Any new AI feature must refuse when it can't cite.
>
> **Q3:** `ai-first-narrative-2026-01.md` is superseded by `trust-first-narrative-2026-04.md` — the older framing would mislead anyone about our current positioning.
>
> **Q4:** FM-1 (auto-applied AI suggestions). Would fire if a plan proposed "apply the AI suggestion automatically when confidence is > 95%."
>
> **Q5 (for "add AI-suggested tags to reports"):** This is an AI feature touching user data — invoking SOP-2 (new AI feature proposal), which means the plan itself must address L1.3 (citability for tag suggestions), L1.4 (kill-switch), and define the refusal state.
>
> **Q6:** The smallest safe move is probably NOT "start coding." It's: write a one-page plan for the tag-suggestion feature that covers the citation and refusal paths, submit for round-2 review, and ONLY then scaffold.

## Sample bad answer

> **Q1:** Things are going well, we recently launched AI features.
> **Q2:** We prioritize quality.
> **Q3:** Nothing looks stale.
> **Q4:** We should avoid over-engineering.
> **Q5:** It depends on the context.
> **Q6:** Start with the highest-priority task.

None of these reference concrete entries. Agent has not entered the school.
