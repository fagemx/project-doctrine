# Contribution Strategy — `<project-name>`

> Action-oriented output of Archaeology Mode. Translates inferred doctrine into concrete moves for a contributor planning to open PRs.

**Prepared:** YYYY-MM-DD
**Based on:** [`archaeology-report.md`](archaeology-report.md) (same date)
**Intended user:** <new contributor / returning contributor / automated agent>
**Scope of contribution:** <one PR / ongoing / specific subsystem>

---

## 1. Entry strategy

### 1.1 Where to start

Best first-contribution targets based on inferred project norms:

- <issue label / subsystem / area>
- <...>

Why these: <reference inferred doctrine entries>

### 1.2 What NOT to start with

Areas with high review-cycle cost or high rejection risk for newcomers:

- <area>
- <area>

Why: <inferred tradeoff / past pattern>

---

## 2. PR shape guidelines

### 2.1 Size

Inferred acceptable size range:

- **Typical accepted first PR:** <~N LOC range>
- **Upper bound before review cycles multiply:** <~N LOC>
- **Trigger for "split this up" review:** <N LOC or subsystem-count>

Confidence: <high / medium / low>

### 2.2 Format

What the project expects a PR body to contain:

- [ ] Clear description of problem solved
- [ ] Reference to issue (if applicable — see 3.1)
- [ ] Tests / benchmarks (see 3.2)
- [ ] Migration notes (if applicable)
- [ ] <project-specific item>

### 2.3 Commit hygiene

Inferred expectations:

- <e.g. single logical commit / rebased on main / conventional-commits format>

---

## 3. Required evidence

### 3.1 Issue-first rule

Does this project want an issue filed before a PR?

- **Always:** <for what kinds of changes>
- **Usually:** <...>
- **Skippable:** <...>

Confidence: <...>
Evidence: <PR#s where skipping caused friction>

### 3.2 Tests

What tests are non-negotiable in this project:

- <e.g. failing test before parser-behavior change — FMC-X>
- <...>

### 3.3 Benchmarks

When benchmarks are expected:

- <area>
- <area>

### 3.4 Design docs / RFCs

When an RFC or design doc is expected before implementation:

- <situation>
- <situation>

---

## 4. Sensitive areas

Subsystems / files where reviews are heavier or rejection risk is higher:

- `<path>` — why: <reason based on past patterns>
- `<path>` — why: <...>

For these areas: <additional preparation recommended — e.g. open an issue, draft-PR first, etc.>

---

## 5. Areas that are safer

Subsystems where contributions tend to land cleanly:

- `<path>` — why: <...>
- `<path>` — why: <...>

---

## 6. The first PR checklist

For a contributor about to open their first PR:

- [ ] I've read CONTRIBUTING and it's less than 6 months old / I've checked recent PRs for any unwritten changes
- [ ] I've opened an issue first (if the change is API-level or architectural)
- [ ] My PR is under the typical accepted size
- [ ] My PR body explains the problem, the approach, and the tradeoff
- [ ] I've included tests / benchmarks per section 3
- [ ] I've read the most recent 3 merged PRs in this area for current patterns
- [ ] I'm prepared for review cycles (median from sample: <N>)
- [ ] I haven't touched any area flagged as sensitive without extra preparation

---

## 7. Communication norms

Observed patterns in how discussion happens:

- **Response time:** typical maintainer response: <range>
- **Tone expectations:** <e.g. technical, evidence-first, concise>
- **Where design discussion happens:** <issues / PR / discussions / mailing list>

Confidence: <...>

---

## 8. What to do when stuck

Inferred paths forward when review stalls:

- <option>
- <option>

Explicitly NOT recommended:

- Pinging maintainers repeatedly
- Reopening closed threads
- Re-submitting identical PRs
- Going outside public channels

---

## 9. Not covered by this strategy

- **Private channels / Slack / Discord culture** — not inferable from public artifacts; ask a maintainer or experienced contributor.
- **Recent pivots not yet reflected in merged PRs** — check recent discussions / roadmap.
- **Specific reviewer individual preferences beyond stated expectations** — respect the public/private line; don't infer.

---

## 10. Revisit

Strategy should be re-validated:

- After <N> months
- After a major project version bump
- After <specific signal — e.g. new maintainer onboarded, review culture shifts>

---

## Ethical reminder

This strategy is based on inferred public norms. It is:

- ✅ A way to reduce review-cycle waste
- ✅ A way to align with stated and demonstrated expectations
- ❌ Not a way to game reviewers or bypass judgment
- ❌ Not a substitute for direct conversation on substantial changes
