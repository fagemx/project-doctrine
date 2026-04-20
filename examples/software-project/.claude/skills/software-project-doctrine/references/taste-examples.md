# Taste Examples — Acme SaaS

## TE-1: AI response copy

**Situation:** User asks the Q&A surface "What were our top 3 customers by spend last quarter?"

**Good:**
> Based on rows 104–247 of `report_q1_2026.csv`:
> 1. Acme Corp — $284,000
> 2. Globex — $219,500
> 3. Initech — $201,200
>
> [View source rows] [Ask a follow-up]

**Bad:**
> 🎯 Great question! Based on my analysis, I'm 92% confident the top 3 customers by spend last quarter were:
> 1. Acme Corp ($284K)
> 2. Globex ($219K)
> 3. Initech ($201K)
>
> Let me know if you'd like me to dig deeper into any of these!

**Why good wins:**
- L1.3 (citability): Good version names the source rows. Bad version has no citation.
- L6.2 (confidence without citation is noise): Bad version's 92% confidence is a false anchor.
- Ops users don't want cheerleading. "Great question!" burns attention without adding value.
- Good version's buttons are the real next actions. Bad version's "let me know" is asking for work the user would have done anyway.

---

## TE-2: Handling an unanswerable query

**Situation:** User asks "Why did our churn spike in March?" The reports contain churn numbers but no attribution data.

**Good:**
> I can't answer that from your current reports. The data shows a churn spike in March (from 2.1% to 4.8%) but doesn't include cancellation reasons.
>
> [Upload exit-survey data] [See churn-only view]

**Bad:**
> Churn likely spiked in March due to several factors including seasonality, competitor pricing changes, and potential product issues. Companies often see elevated churn in Q1 due to budget cycles.

**Why good wins:**
- L1.3: Bad version fabricates. None of the "likely factors" are grounded in the user's data.
- L1.1 (trust > speed): Good version refuses; bad version guesses. For ops, a refusal is more useful than a confident fabrication.
- The buttons in the good version give the user a path forward without pretending the AI knows things it doesn't.

---

## TE-3: Adding a new AI feature

**Situation:** PM proposes "AI-suggested report templates" — when a user starts a new report, suggest a template.

**Good plan:**
- Feature-flagged (kill-switch: tested in staging under realistic load)
- Citation-like provenance: "Suggested because your team has used this template 12 times in the last 90 days"
- User explicitly picks a template — no auto-fill
- Fallback: if confidence is low, suggest "blank" instead of a bad template
- Rollout: 5% → 25% → 50% → 100% over 3 weeks, gated on user-correction rate

**Bad plan:**
- Ship behind a flag but skip the "off state tested" step
- Auto-populate the report with the highest-confidence template
- Show "98% match" next to the suggestion
- Rollout: ship to everyone, watch for complaints

**Why good wins:**
- L1.2 (AI proposes, user decides): Good version requires a click; bad version auto-fills.
- L1.4 (kill-switch before kill): Bad version ships a flag without exercising it — rerun of FM-4.
- L6.4 (user's undo is real undo): Auto-populating forces users into a bigger undo path.
- L6.2: 98% match without source is noise — the bad version reruns the exact pattern we just removed.

---

## Maintenance

- New entry when a PR review produces a "no, not like that" generalizable moment
- Retire when the underlying L1 shifts
- 3–10 entries is a healthy range for a product of this size
