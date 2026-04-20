# Review Risk Map — `<project-name>` / `<proposed-change-name>`

> Forward-looking risk analysis for a **specific planned change**, using inferred doctrine to predict where review friction is most likely.

**Prepared:** YYYY-MM-DD
**Prepared by:** <name or agent>
**Based on:** [`archaeology-report.md`](archaeology-report.md)
**Change scope:** <describe the proposed change in 2–3 sentences>

---

## 1. Change summary

- **Problem this solves:** <one sentence>
- **Approach:** <one sentence>
- **Files / subsystems touched:** <list>
- **LOC estimate:** <range>
- **Breaking changes:** <yes / no / partial>
- **Linked issue:** <#N or "none">

---

## 2. Size risk

Inferred size norm for this project: <range from archaeology-report>

**This change vs norm:**
- Smaller than norm — low risk
- Within norm — low risk
- Larger than norm — flag
- Much larger — **high risk of "split this up" review**

**Mitigation (if oversized):**
- Can this be split into N sequential PRs? <yes / no, with plan>
- Is there a natural seam (data layer → API → UI)?

---

## 3. Scope risk

Does the change span concerns or stay narrow?

- Single concern / narrow — low risk
- Two related concerns — medium
- Cross-cutting — **high risk of "not the project's style" review**

**Mitigation:** identify the minimum scope that still delivers value.

---

## 4. Subsystem sensitivity

From Archaeology Mode, subsystems flagged as sensitive. Check this change against them:

| Subsystem | Touched by this change? | Inferred sensitivity | Mitigation |
|---|---|---|---|
| <e.g. parser core> | yes / no | high | <open issue first / draft PR / RFC> |
| <e.g. public API> | yes / no | high | <migration path required> |
| <generated files> | yes / no | — | <should not be modified> |

---

## 5. Evidence requirements

Cross-reference this change against the project's evidence expectations:

- [ ] **Tests:** required kinds present? <yes / no — list missing>
- [ ] **Failing test first** (if applicable to this subsystem): <yes / no>
- [ ] **Benchmark:** required? <yes / no / optional>
- [ ] **Migration notes:** required for BC-breaking changes
- [ ] **Design doc / RFC:** required for changes at this scope?

Any "no" on a required item → **high risk**.

---

## 6. Repeated review concerns likely to apply

Walk the list of repeated review concerns from `archaeology-report.md` section 3. For each, mark risk to this change:

| Concern | Applies to this change? | Risk level | Pre-addressed? |
|---|---|---|---|
| Scope too large | | | |
| Missing tests | | | |
| Backward compatibility | | | |
| Performance | | | |
| API design | | | |
| Maintainability | | | |
| Security / trust boundary | | | |
| Documentation | | | |
| User experience | | | |
| Project-direction mismatch | | | |

Each unaddressed concern = review cycle.

---

## 7. Communication plan

Based on change risk:

- **Low risk** (small, narrow, in safe subsystem): open PR directly.
- **Medium risk:** open a brief issue first, link in PR.
- **High risk:** issue + draft PR + explicit call-out to relevant area's reviewers (respecting the project's pinging norms).
- **Very high risk (architectural):** RFC first, then implementation PR.

**Decision for this change:** <which path, why>

---

## 8. "What would this project refuse?"

Walk the project's refused-directions list (archaeology-report section 2.3). Does this change resemble any of them?

- <refused direction>: this change does / does not resemble it because <reason>
- <refused direction>: ...

If any match is "does resemble": reconsider the approach, or prepare the argument for why this case is different.

---

## 9. Positive signals

Mirror-image of refused directions: does this change match the project's "good shape" patterns?

- <good-shape pattern>: this change does / does not match because <...>

Leverage matches in the PR description.

---

## 10. Expected review cycles

Based on the sample's median for similar changes:

- Median cycles: <N>
- Expected range: <N–M>
- Signals that would extend: <...>
- Signals that would accelerate: <...>

Plan time accordingly. Don't push for faster than the project's norm.

---

## 11. Pre-PR checklist

- [ ] Change is within size norm (or explicitly split)
- [ ] Issue opened if required
- [ ] Required tests / benchmarks / migration notes present
- [ ] Checked against refused-directions list (section 8)
- [ ] Read recent 3 merged PRs in touched area
- [ ] PR description covers: problem, approach, tradeoff, evidence
- [ ] Author is prepared for <N> review cycles

---

## 12. If rejected or heavily revised

Possible outcomes:

- **"Split this up"** → execute the split plan from section 2
- **"Not the right direction"** → step back, open design issue
- **"Missing evidence"** → add the evidence; usually salvageable
- **"Touches sensitive area wrongly"** → rework the approach, not just the code

None of these are failures — they are review-cycle outcomes. Plan for them.

---

## Ethical reminder

This map predicts friction based on **public patterns**. It is:

- ✅ A way to reduce review-cycle waste
- ❌ Not a guarantee of acceptance
- ❌ Not a strategy for working around the project's judgment
- ❌ Not an attempt to predict individual reviewer reactions beyond their stated expectations
