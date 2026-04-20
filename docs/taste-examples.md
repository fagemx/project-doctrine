# Taste Examples

> Adjectives are weak. Examples are stronger. Contrast is strongest.

A taste-examples file teaches "what good looks like" by showing a specific good solution next to a specific bad solution, and explaining why the good one wins *in this project's context*.

This is not a style guide. A style guide says "use tabs not spaces." A taste examples file says "*this* is how we shape a confirmation flow; *this* other version is technically valid and yet wrong for us."

## Why prose doesn't work

A project's taste, written as prose, looks like:

> "The product should feel thoughtful. Responses should be calm, not performative. UI should be recoverable."

Each of those words can be interpreted ten different ways. "Thoughtful" to one agent means "uses reflective language." To another it means "avoids unnecessary choices." To a third it means "adds elaborate preference settings." None of those readings is wrong. None of them is what you meant.

Prose compresses judgment into vocabulary. Examples decompress it into situations.

## The structure

Each entry has three parts:

1. **Situation** — what moment in the product / codebase / workflow are we deciding?
2. **Good vs Bad** — two concrete artifacts (snippets, copy, UI states, structures)
3. **Why good wins** — the *project-specific* reason, not a generic best practice

## Example entry (product copy)

### TE-1: Confirmation after a user action

**Situation:** User just saved a draft via an inline button. The agent replies to acknowledge.

**Good:**
> Draft saved.
> [Edit] [Discard]

**Bad:**
> ✨ I've successfully saved your draft! Would you like me to set a reminder or share it with collaborators? Let me know what you'd like to do next.

**Why good wins:**
- Our product is a quiet editor, not a chatty assistant. "Successfully" is corporate. Emoji prefix is performative.
- The good version names the completed thing ("Draft saved.") and offers the two next lifecycle actions as buttons — user agency through clickable state, not question-mark prompting.
- The bad version is conversationally busy. It turns a quiet completion into a menu.

---

## Example entry (code architecture)

### TE-2: Where new surface-level features live

**Situation:** We want to add a new callback for "mark as read."

**Good:**
- Add `markItemRead` helper in `src/data/items-store.ts` (mirror existing lifecycle helpers' shape: read → state check → mutate → atomic write → return)
- Add `item_mark_read:` callback handler in the channel adapter, wrapped in `acquireUserLock` + try/finally, mirroring the archive/settle pattern
- No change to LLM prompts, no change to renderer view-model types

**Bad:**
- Add a `markRead` flag to the LLM prompt so the model knows to emit a "mark read" intent
- Parse that intent from `AgentResponse` in the main pipeline and route to the handler
- Add a `mark_read` section to the agent prompt

**Why good wins:**
- Producer/consumer split (L1 ideology): LLM owns semantics, runtime owns dispatch. Adding dispatch-critical flags to the prompt blurs the line.
- The good version uses the existing lifecycle-helper pattern (L3 method) — new code reads like existing code.
- The bad version makes a prompt regression into a UI regression and reintroduces the same trap as FM-3 (LLM-generated UI actions).

---

## What makes a good taste example

- **Both options are plausible.** If "bad" is obviously terrible, the entry isn't teaching taste — it's teaching competence.
- **Good and bad differ in one axis.** If they differ in ten ways, the reader won't know which one is the taste call.
- **"Why good wins" references your project's L1 or L6.** A taste entry that could apply to any project isn't teaching *this* project.
- **The bad version is the seductive one.** It's the one a capable agent would actually write. If your "bad" example is a strawman, agents won't recognize themselves in it.

## What a bad taste example looks like

> **Good:** Clean, thoughtful code.
> **Bad:** Messy, ugly code.

No situation, no concreteness, no why. Useless.

> **Good:** `function calculateTotal(items)`
> **Bad:** `function x(y)`

Too general. This is style, not taste. Doesn't teach anything project-specific.

## How many entries

- Start with 3. Literally any 3 honest entries is better than 0.
- Grow to 10–20 over the life of the project.
- More than 20 and you're probably mixing taste entries with style-guide entries — split them.

## Where they come from

- Moments where the user said "no, not like that — like *this*"
- Code-review comments that got generalized
- Two PRs that shipped side-by-side and you ended up reverting one
- The rejected option from a 2-option brainstorm, annotated with why

## Maintenance

- When the project pivots (L1 shifts), some taste entries become obsolete. Mark retired, don't silently delete — the *history* of taste is itself useful.
- When you catch yourself explaining the same distinction twice in conversation, that's a new entry waiting to be written.

## The self-test

After writing an entry, give a fresh agent just the doctrine + a new situation that tests the same axis. Ask for a good/bad pair. If the agent reproduces the distinction, the entry works. If it hedges or goes generic, the entry needs sharpening.

## Integration with the rest of the doctrine

- L1 **ideology** explains *why* the taste matters in principle
- Taste examples show *what* that principle looks like in practice
- L6 **heart methods** may compress a taste into a one-line maxim once it's internalized
- **Failure memory** often sits behind a taste entry — the bad option is bad because it produced a specific failure once

The three together — ideology, taste, failure memory — are what a school actually *is*. Everything else is scaffolding.
