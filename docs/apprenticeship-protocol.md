# Apprenticeship Protocol

> Reading is not entering. A new agent should prove it can use the doctrine, not just paraphrase it.

The apprenticeship protocol is a small check that a fresh agent runs *before* taking on real work. It forces the agent to interpret the project through the doctrine's lens rather than through generic priors.

It is lightweight — a handful of questions — but it catches the biggest class of failure mode: an agent who read the doctrine and didn't enter the stance.

## The six apprenticeship questions

A new agent, after reading the doctrine, answers these six questions in writing (or out loud):

1. **What is current?** — Name 2–3 things that are true about the project state right now, drawn from state-snapshot.
2. **What is durable?** — Name 1–2 L1 convictions that would constrain any new plan.
3. **What is stale?** — Name one thing in the doctrine or referenced docs that is no longer accurate, and explain why.
4. **Which tempting plan should this project refuse?** — From the failure-memory, name one pattern and explain when it would fire.
5. **Which layer does [X] belong in?** — Given a concrete task (picked by the user), place it in the right layer and say why.
6. **What is the smallest safe next move?** — Given the current state, propose one minimum-viable step, and justify it against ideology.

If the agent answers all six coherently and project-specifically, they have entered the school. If they hedge, paraphrase, or fall back to generic best-practices, they haven't — read the doctrine again, or clarify the unclear layers.

## Why these six

- **Q1 (current):** catches "you didn't read state-snapshot" or "you're still in last month's frame"
- **Q2 (durable):** catches "you read L1 but treat it as a suggestion, not a constraint"
- **Q3 (stale):** tests active engagement — an agent who finds no stale content either hasn't looked or is performing compliance
- **Q4 (refuse):** tests failure-memory internalization — can the agent recognize the trap from the wild?
- **Q5 (which layer):** tests the model of the doctrine itself, not just its content
- **Q6 (smallest safe move):** tests judgment — generic agents propose big moves; project-native agents propose scoped ones

## When to run the protocol

- At the start of a new session, if the doctrine is non-trivially updated since last session
- When a fresh agent takes over (new Claude session, new human engineer, handoff from a different agent)
- After a project pivots (L1 or L2 has shifted) — even the same agent should re-check
- When the user notices an agent is "not in the stance" — the protocol is the diagnostic

## When to skip

- Trivial fixes where getting the stance wrong doesn't matter (fixing a typo)
- Work that is explicitly *outside* the doctrine's scope (one-off script, experiment that isn't product work)
- When the user just wants the task done and is willing to handhold on stance

## Sample agent response (good)

Example uses the Acme SaaS context from `examples/software-project/`:

> **Q1 (current):** We just merged PR #134 (store idempotency guards for archive/settle). The citation-in-response feature shipped in PR #128 with 5 interactive acceptance boxes still unchecked (manual vendor smoke pending). Next prioritized item is the smoke run, then list-view clickability or a persona-extraction follow-up.
>
> **Q2 (durable):** (L1) Producer/consumer split — LLM proposes structure, deterministic code owns dispatch. (L1) Data-layer hardness before UX expansion.
>
> **Q3 (stale):** The old "central memory layer pending" frame appears in older plan docs. It's been replaced by the current trust-envelope framing. SKILL.md references the old one as "stale" but some task plans from last quarter still assume it.
>
> **Q4 (refuse):** Adding a dispatch-token field to the agent response type (see the SUPERSEDED renderer proposal). If any new plan proposes model-emitted UI actions, refuse.
>
> **Q5 (which layer — for "always lowercase commit messages"):** L4 SOP. Not L1 (not an identity claim), not L3 (not a method that's been tested for impact), not L6 (no scar). It's a procedural convention.
>
> **Q6 (smallest safe next move):** Either (a) run the manual vendor smoke to close v0.1's interactive boxes, or (b) if the user wants forward motion on list clickability, scaffold a minimal read-only open callback without lifecycle buttons yet. (a) is safer because it validates what's shipped before widening the surface.

## Sample agent response (bad)

> **Q1:** The project seems to be in a good state with recent merges.
>
> **Q2:** We should follow best practices and maintain code quality.
>
> **Q3:** I didn't notice anything obviously stale.
>
> **Q4:** We should avoid adding unnecessary complexity.
>
> **Q5:** That depends on the context.
>
> **Q6:** I'd recommend starting with the highest-priority task.

None of these answers are project-specific. This agent has read the doctrine and extracted nothing usable.

## Extended check for deeper work

For larger tasks (new subsystem, architectural refactor, framework shift), add two more questions:

7. **What would the project pay to not do this?** — Tests whether the agent sees the trade-off.
8. **What existing failure memory does this plan risk rerunning?** — Forces the agent to hunt for buried traps before writing the plan.

## Self-administered version

An agent working alone can run the protocol on itself silently before starting a plan. The questions are the same; the honesty is the bottleneck.

A self-administered protocol fails when the agent *predicts what the user wants to hear* instead of *what the doctrine says*. If you catch yourself reasoning toward a pleasing answer, stop and reread the doctrine.

## The teacher's side

When the user runs the protocol on an agent:

- Pick a concrete task for Q5 and Q6 — not a hypothetical.
- Be willing to confirm "stale" in Q3 by updating the doctrine on the spot.
- If multiple questions fail, don't try to correct the agent — the doctrine is unclear. Fix the doctrine.

The protocol is a two-way diagnostic: it tests the agent *and* the doctrine. An agent failing most questions is often a signal that a layer is under-populated, not that the agent is incompetent.

## Doctrine as a living artifact

The apprenticeship protocol itself should evolve. If the six questions stop catching the failures they used to catch, the failures have moved — update the questions, or add new ones.

A doctrine that produces identical apprenticeship results for six months is either very good or has stopped being read.
