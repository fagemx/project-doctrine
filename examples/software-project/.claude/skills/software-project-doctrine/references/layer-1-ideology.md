# L1 — Ideology (Acme SaaS)

## 1.1 — Trustworthy first, fast second

**Claim:** When speed and trust conflict, trust wins. Every time.

**Why:** We serve ops teams running compliance-adjacent workflows. A fast-but-wrong answer costs them hours of rework and their credibility with their auditors. Our product's value collapses the moment users stop trusting our output.

**Violation test:** A plan proposes shipping an AI feature before its refusal path is defined, or proposes silencing a warning signal to reduce noise.

## 1.2 — AI outputs are proposals, not decisions

**Claim:** The LLM proposes; the user decides. No AI-initiated writes to customer data.

**Why:** Early prototype (2026-01) auto-applied AI suggestions. We rolled it back after 3 users lost an afternoon re-reverting changes. We concluded: when AI is wrong, the cost of undo must be small. Cheapest undo is "the user never clicked apply."

**Violation test:** Any code path where an AI output mutates user-visible state without an explicit user action between generation and persistence.

## 1.3 — Every AI answer must be citable

**Claim:** If the AI cannot cite the source row(s), it should say "I cannot answer that" instead of guessing.

**Why:** Our users' work product is held to audit standards. An uncitable answer is worse than no answer.

**Violation test:** A response in production without citation attached, OR a plan that lowers the citation-coverage threshold for any query class.

## 1.4 — Kill-switch before kill

**Claim:** Every AI feature ships with a kill-switch documented and tested, before the first user sees it.

**Why:** The 2026-04-08 vendor incident cost us six hours of degraded service because the kill-switch existed but had never been exercised. Now we exercise it during rollout, not after.

**Violation test:** A new feature flag that hasn't been tested in its "off" state under production-like load.

---

## Changelog

- `2026-01-18` — Founding L1.1 (trust > speed), L1.2 (AI proposes, user decides).
- `2026-03-15` — Added L1.3 (citability). Reason: Q&A launch required it.
- `2026-04-10` — Added L1.4 (kill-switch discipline). Reason: 04-08 incident.
