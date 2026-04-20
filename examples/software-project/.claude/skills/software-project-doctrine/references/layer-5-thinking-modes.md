# L5 — Thinking Modes (Acme SaaS)

## 5.1 — Refusal-first design

**What it is:** When proposing an AI feature, design the "I can't answer that" path first — before designing the happy path.

**When to enter it:** Any time you're sketching a new AI-driven capability.

**How to hold it:**
- Start by naming the inputs that should produce a refusal
- Define what the refusal UI looks like
- Only then design the successful-answer UI

**How to notice you've dropped it:** The plan has a clear happy path and a vague "handle edge cases" note for refusal.

---

## 5.2 — Trust-envelope check

**What it is:** Before committing to an AI behavior, ask where it sits in the trust envelope — is this an advisory, a proposal, or a decision?

**When to enter it:** Every architecture / plan / UX decision involving AI output.

**How to hold it:**
- Advisory = AI suggests, user reads, nothing happens
- Proposal = AI suggests, user explicitly accepts, change commits
- Decision = AI triggers a state change without user action — NOT ALLOWED (L1.2)

**How to notice you've dropped it:** You're using phrases like "the AI will automatically..." without naming which envelope layer that sits in.

---

## 5.3 — Framing before tuning

**What it is:** When AI output quality is disappointing, ask whether the framing is right before reaching for a bigger model or more prompt rules.

**When to enter it:** Any moment you consider adding a prompt rule, switching to a larger model, or adding few-shot examples.

**How to hold it:**
- State what the model is being asked to produce
- State what the model is being given
- Ask: is there a different shape of the same task that would be easier?

**How to notice you've dropped it:** Prompt is getting longer. Rules are stacking. Quality is flat.

---

## 5.4 — User-correction ground truth

**What it is:** Treat user corrections of AI output as ground truth, not as noise.

**When to enter it:** Weekly quality review; any time a vendor benchmark says one thing but user data says another.

**How to hold it:**
- Look at correction patterns before looking at benchmark scores
- If benchmarks and corrections disagree, trust corrections
- Ask: what would have to be true about the world for this correction to be the user's fault?

**How to notice you've dropped it:** You're defending an AI output by citing a benchmark rather than investigating why the user corrected it.
