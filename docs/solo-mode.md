# Solo Mode

> **For solo builders and future-you.**
>
> A doctrine is a memory prosthetic for your future self and your agents.

Solo Mode is the simpler of the two usage modes. One person, one or more AI agents, a project that has accumulated enough judgment to be worth preserving.

## When Solo Mode fits

Use Solo Mode when:

- You are the main builder
- You work with AI agents (Claude Code, Cursor, Codex, etc.) across long sessions
- You return to projects after gaps and keep losing context
- Multiple agents keep making the same wrong assumptions about the project
- Handoffs explain what happened but not why it matters
- Your project has taste or philosophy that normal docs do not capture

**Solo Mode's core question:**

> How does future-me (plus the agents I'll be working with) avoid relearning what current-me already paid for?

## What makes Solo Mode different

Solo doctrine can be **more personal and opinionated** than team doctrine. You're writing for yourself and your agents, not for onboarding teammates or passing architecture review.

You are allowed to write things like:

> I keep being tempted to turn this into a productivity bot. Do not let that happen.

or:

> This project should feel like a room that remembers, not a task manager with a mascot.

These kinds of entries would be inappropriate in team doctrine (too subjective, not collectively negotiated). In solo mode, they are precisely the point: your taste, your conviction, in your voice.

## File structure (solo)

```
docs/skills/<your-project>-doctrine/
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

Or equivalently in `.claude/skills/` if you want it auto-loaded by Claude Code.

## Minimum viable solo doctrine

Solo projects don't need all 12 files on day 1. A working v0 can be as small as:

- `state-snapshot.md`
- `layer-1-ideology.md`
- `layer-5-thinking-modes.md`
- `layer-6-heart-methods.md`
- `failure-memory.md`
- `bootstrap-prompt.md`

If you're short on time, write these four things:

1. **What this project cannot become** (L1)
2. **What AI agents most often misunderstand about this project** (failure-memory)
3. **What the project's current state actually is** (state-snapshot)
4. **What mistakes not to make again** (L6 + failure-memory)

Leave L3 (methods) and L4 (SOPs) for later. They populate themselves as you validate work patterns.

## When to update (solo)

Solo doctrine has **low ceremony**. You don't need PRs or reviews. Update in-session when:

- You finish a non-trivial feature
- An AI agent misunderstands the project in a way you recognize as systemic
- You change direction on the product
- A plan gets thrown out
- A mistake costs real time
- A new maxim emerges ("oh, the lesson here is X")
- You notice old handoffs starting to mislead new sessions

You don't need to update weekly. You just need to update when something **shifted**.

## Writing style (solo)

- **You can be subjective.** "I don't trust this path" is valid.
- **You can be terse.** No need to explain to strangers.
- **You can swear.** (If that's you.)
- **You can be bilingual.** Whatever compresses the thought tightest.

The only rule: the entry has to **fire** when future-you reads it. If the voice wouldn't trigger the right attention in three months, rewrite.

## Failure memory in solo mode

Solo failure-memory can name specific bad moves without worrying about blame (since the only person to blame is you).

Write entries like:

> **FM-2: Over-engineering the storage layer before traffic existed**
>
> **Temptation:** The data model "obviously" needed versioning, so I built a v1/v2 migration framework before there was any v1 data worth migrating.
>
> **How it failed:** Spent 3 days on abstractions that were never exercised. When real traffic arrived 2 months later, the actual migration need was completely different.
>
> **Future detection:** Any week where my plan contains "migration" but no current user is affected.
>
> **Correct move:** YAGNI until there's evidence of need. Store → migrate when migration is forced.

Direct, specific, first-person-honest.

## Taste examples in solo mode

Solo taste examples often preserve the aesthetic the project is reaching for — the thing a style guide can't capture because it's not about style.

> **TE-1: What an acknowledgment should feel like**
>
> **Situation:** User says "it's fine, not urgent." The agent acknowledges.
>
> **Good:**
> "OK."
>
> **Bad:**
> "Understood — I'll keep this in mind for when it becomes relevant. Let me know if the timing changes."
>
> **Why good wins:** The project values low-friction acknowledgment over performative helpfulness. The bad version is fluent and technically kind, but it triples the length without adding anything. Short acknowledgment matches the project's stance against over-explaining.

This kind of taste call is hard to write as team doctrine (too dependent on the author's ear). Solo mode can capture it directly.

## What's different if you later move to Team Mode

If your project grows a team, the solo doctrine is a starting point but needs changes:

- **Personal voice → shared voice.** Entries that read as "I don't like this" need to become "this project refuses this because X."
- **Subjective taste → contrastive taste.** "It should feel right" won't survive team review; concrete good/bad pairs will.
- **Failure memory → de-personalized.** Even in solo mode, de-personalizing failure memory from day 1 makes the team transition easier.
- **Add governance.** Someone needs to own doctrine changes. In solo mode, that's you by default. In team mode, it must be explicit.
- **Add decision records.** "Why we decided this" becomes important once multiple people need to not re-litigate the decision.

The structure stays. The writing discipline tightens.

## Anti-patterns in solo mode

- **Journal-style.** Doctrine isn't a dev log. "Today I worked on X" is not a doctrine entry.
- **Motivational slogans.** L6 requires a scar. "Stay focused" is not L6.
- **Aspirations disguised as L1.** "I want to ship every week" is a goal, not a durable conviction.
- **Stale state-snapshot.** Solo mode's biggest failure mode — the state-snapshot that's 6 months old but still looks current.

## The solo-mode self-test

Every few weeks, pretend you're a fresh agent reading the doctrine for the first time. Can you answer the apprenticeship-check questions from the doctrine alone? If not, something's under-populated.

If you CAN, but the answers sound generic, the doctrine is technically complete but not yet sharp. Push on specificity.

## Why bother, as a solo builder?

Because you are the lossiest memory system in the project. Your brain six months from now is already a different version of you. The agents you'll work with in three sessions from now will have no idea what you learned yesterday.

Solo doctrine is the thing that makes "coming back to a project" feel like **returning** instead of **restarting**.

## One-sentence definition

> Solo doctrine is the contract between current-you, future-you, and every agent you will ever dispatch into this project.
