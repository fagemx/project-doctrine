# State Snapshot — Acme SaaS

**Last reviewed:** 2026-04-18
**Reviewer:** @teamlead

## Current phase

Post-launch hardening. AI features (Q&A over reports) shipped 2026-03; we are now improving the *confidence* surface — users don't trust answers yet, so they double-check manually, eroding the value prop.

## Recently shipped (last 5 things)

- `2026-04-15` — Citation-in-response feature (every AI answer cites source rows)
- `2026-04-10` — Refusal path: AI says "I can't answer that from your data" instead of guessing
- `2026-04-03` — Telemetry on user corrections of AI answers (a new taste signal)
- `2026-03-28` — Feature flag wrapper for all AI features (kill-switch in < 5 min)
- `2026-03-20` — Q&A over reports (MVP)

## Actively in progress

- **Confidence calibration** (@eng1) — mapping LLM self-reported confidence to user-correction rate
- **Plan-review loop** (@eng2) — bringing subagent-driven-development to the core repo
- **On-call runbook for AI outages** (@pm1) — user-facing comms when OpenAI degrades

## Blocked / deferred

- Fine-tuning pilot — blocked on legal review of training data
- Slack integration — deferred to Q3 (priority conflict)

## Hard boundaries right now

- No new AI features until citation coverage ≥ 95%
- No model downgrades without user communication
- No silent fallback from primary model to secondary — always surface it

## What to ignore (stale frames)

- The "AI-first" product frame from 2026-01 — we're now "trust-first, AI-assisted"
- The old `summarize_report_v1` endpoint — deprecated 2026-04-05

## Current architecture source-of-truth

- `docs/architecture/ai-trust-envelope-v2.md` — how we bound AI output
- `docs/architecture/citation-pipeline.md`
- `docs/architecture/kill-switch-protocol.md`

## Current open questions

- Should we expose model version in the UI? (@pm2 investigating)
- How do we handle AI-generated explanations that are correct but condescending?

## Recent scars worth preserving in L6

- `2026-04-08` incident: model started refusing safe queries after a vendor update. Took 6 hours to detect because our smoke tests ran against a mock. → L6 candidate: "smoke tests must hit the real thing, not a contract."
