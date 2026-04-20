---
name: software-project-doctrine
description: Project posture loader for Acme SaaS. Load before planning, reviewing, or making non-trivial decisions.
load-protocol:
  - references/state-snapshot.md
  - references/layer-1-ideology.md
  - references/layer-5-thinking-modes.md
  - references/layer-6-heart-methods.md
on-demand:
  - references/layer-2-knowledge.md
  - references/layer-3-methods.md
  - references/layer-4-sops.md
  - references/failure-memory.md
  - references/taste-examples.md
  - references/apprenticeship-check.md
  - references/bootstrap-prompt.md
  - references/provenance.md
---

# Acme SaaS Doctrine

## What this is

The posture loader for Acme SaaS. Read before writing a plan, reviewing a PR, or making an architectural move. Do NOT summarize this back; enter the stance.

## Load protocol

1. `references/state-snapshot.md` — current state
2. `references/layer-1-ideology.md` — durable convictions
3. `references/layer-5-thinking-modes.md` — how we reason
4. `references/layer-6-heart-methods.md` — compressed scars

On-demand: the rest.

## One-sentence identity

Acme helps B2B ops teams run their weekly reporting with AI assistance. Our product's job is to be *trustworthy first, fast second*.

## Conventions

- Changes land as PRs to `main` via squash-merge.
- AI features are gated behind a feature flag until their failure-mode envelope is documented.
- Agent-initiated changes must reference a plan doc in the PR body.

## Closing

Doctrine > handoff. If doctrine and evidence conflict, trust evidence and patch the doctrine.
