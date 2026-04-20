# L6 — Heart Methods (Acme SaaS)

## 6.1 — Smoke tests must hit the real thing

**Scar:** 2026-04-08 — Vendor model started refusing safe queries. Our smoke tests ran against a mocked LLM that still returned 200. Customer-facing detection took 6 hours. Cost: two angry support calls, one postmortem Slack channel.

**Triggers when:** A PR proposes adding mocks to a path that talks to a vendor. First ask: is this actually mockable without defeating the purpose?

## 6.2 — Confidence without citation is noise

**Scar:** Early Q&A (pre-March) returned "I am 90% confident" with no source. Users trusted the confidence number more than they trusted their gut. When the AI was wrong, they were more wrong than if they'd had no help.

**Triggers when:** Any UI element displays an AI confidence number. First ask: is a citation attached? If not, the confidence is lying.

## 6.3 — Kill-switch is exercised, not just documented

**Scar:** 2026-04-08 again. The kill-switch existed. No one had run it under load. When we finally flipped it, it also killed the citation pipeline, which also killed the refusal path. Cascade.

**Triggers when:** Launching a new feature-flagged feature. First ask: has the "off" state been tested under production-like conditions? Not "is the code present" — "has it been run."

## 6.4 — The user's undo is the real undo

**Scar:** 2026-01 prototype auto-applied suggestions. Our "undo" was a support ticket. The real undo was the user pasting back their old data from a screenshot. We learned the undo that matters is the one the user executes, in the product, in under 10 seconds.

**Triggers when:** A feature proposes any auto-action on user data. First ask: can the user undo this in their own hands in < 10s?

## 6.5 — Framing > model capacity

**Scar:** Spent two weeks in March trying to make GPT-5 answer better questions on our data. Problem wasn't the model. The questions we were letting users ask were under-specified. Reframing the prompt (from "answer X" to "identify what's missing to answer X") reduced hallucination by 40% overnight.

**Triggers when:** You catch yourself trying a bigger model or more prompt tuning. First ask: is the frame right?

---

## Provenance

Each entry references its originating incident. See `references/provenance.md` for full audit trail.
