# L2 — Knowledge (Acme SaaS)

## Reading ladder for a new session

1. `references/state-snapshot.md`
2. `docs/architecture/ai-trust-envelope-v2.md` — canonical trust model
3. `docs/architecture/citation-pipeline.md` — how citations attach to AI outputs
4. `docs/architecture/kill-switch-protocol.md` — feature-flag discipline

On demand:

- `docs/runbooks/oncall-ai-outage.md` — when a vendor degrades
- `docs/retrospectives/2026-04-08-vendor-refusal-incident.md` — the scar behind L6.1
- `docs/product/ops-user-interview-2026-Q1.md` — where "trust > speed" L1.1 comes from

## Canonical specs

| Path | Description | Last verified |
|---|---|---|
| `docs/architecture/ai-trust-envelope-v2.md` | Trust boundaries for AI outputs | 2026-04-12 |
| `docs/architecture/citation-pipeline.md` | Citation attachment flow | 2026-04-15 |
| `docs/architecture/kill-switch-protocol.md` | Feature-flag discipline | 2026-04-11 |

## Superseded docs (do not follow)

| Path | Replaced by | Superseded on |
|---|---|---|
| `docs/architecture/ai-trust-envelope-v1.md` | `-v2.md` | 2026-04-01 |
| `docs/product/ai-first-narrative-2026-01.md` | `trust-first-narrative-2026-04.md` | 2026-04-05 |

## Source-of-truth for common questions

- **What's our trust model?** → `ai-trust-envelope-v2.md`
- **How do citations work end-to-end?** → `citation-pipeline.md`
- **What's our incident comms template?** → `docs/runbooks/incident-comms.md`
- **Who owns the kill-switch?** → @eng1 (primary), @eng2 (backup)
