# Archaeology Report — `<project-name>`

> **Analyze decisions, not personalities. Infer norms, not motives.**

Per-project doctrine brief, inferred from public artifacts (PRs, issues, reviews, release notes). Every entry carries a confidence level and evidence. Un-scored claims are removed.

**Report compiled:** YYYY-MM-DD
**Compiled by:** <name or agent session>
**Scope:** <subsystem / full project>
**Sample size:** <N merged PRs + N rejected PRs + N heavily-reviewed PRs + N issues>

---

## 1. Explicit doctrine (what the project already states)

Summarize `README`, `CONTRIBUTING`, `docs/`, `GOVERNANCE`, `ROADMAP`.

- Stated identity: <one line>
- Stated contribution norms: <bullets>
- Stated tradeoffs / priorities: <bullets>
- Date / version of canonical docs: <note any staleness>

---

## 2. Project doctrine brief (inferred)

### 2.1 Identity

**Claim:** What the project seems to believe it is for — beyond the README.
**Confidence:** high / medium / low
**Evidence:** <PRs, issues, release-note framings>

### 2.2 Core tradeoffs

Repeated choices between competing values. For each:

**Tradeoff:** <e.g. "safety over speed" or "narrow patch over broad refactor">
**Confidence:** high / medium / low
**Evidence:** <PR#s, review comments>

### 2.3 Directions the project refuses

Things that come up and keep getting declined:

- **Direction:** <e.g. "large cross-cutting refactors without a concrete bug fix">
  **Confidence:** ...
  **Evidence:** ...

### 2.4 What counts as "good" here

Inferred good-shape signals:

- <pattern>
  **Confidence:** ...
  **Evidence:** ...

### 2.5 What counts as "wrong shape" here

Inferred bad-shape signals:

- <pattern>
  **Confidence:** ...
  **Evidence:** ...

---

## 3. Decision patterns (NOT personality)

> Patterns in how the project decides. Describes the decision-making as evident from public artifacts. Does NOT profile specific people's psychology.

### 3.1 Scope handling

How does the project handle scope-creep, large PRs, multi-concern changes?

**Pattern:** <description>
**Confidence:** ...
**Evidence:** ...

### 3.2 Evidence expectations

What evidence do reviewers consistently ask for?

- Tests: <required / optional / required for X but not Y>
- Benchmarks: <...>
- Migration path: <...>
- Design doc / RFC: <when required>

**Confidence:** ...
**Evidence:** ...

### 3.3 Backward compatibility stance

How strict is the project about BC? What exceptions have been made?

**Pattern:** ...
**Confidence:** ...
**Evidence:** ...

### 3.4 Review cycles and turnaround

Characterized, not personalized:

- Typical cycles before merge: <median, from sample>
- What tends to extend review time: <patterns>
- What tends to accelerate: <patterns>

**Confidence:** ...
**Evidence:** ...

### 3.5 Reviewer expectations (public, evidence-based)

If naming individuals, only describe observable expectations from their public comments. NOT their personality, motives, or private preferences.

**Good form:**
> Reviewer @X consistently requests benchmarks for parser changes (PRs #201, #245, #311). Expectation is established, not surprise.

**Not acceptable:**
> Reviewer @X "prefers control" or "finds complexity stressful."

---

## 4. Failure-memory candidates

Patterns that consistently **fail review**. (Not about the project failing — about contributions that fail.)

### FMC-1: <name>

- **Temptation:** <why a contributor would try this>
- **How it fails in this project:** <what reviewers flag>
- **Future detection:** <signal to notice before opening the PR>
- **Correct move:** <what shape the project actually accepts>
- **Confidence:** ...
- **Evidence:** ...

(Repeat for each pattern.)

---

## 5. Taste-example candidates

Good/bad contrast pairs from actual PRs.

### TC-1: <situation>

- **Situation:** <what kind of change this is>
- **Good (this project's taste):** <describe or link a PR that exemplifies it>
- **Bad (rejected or heavily revised):** <describe or link>
- **Why good wins here:** <project-specific reason based on stated identity / repeated tradeoffs>
- **Confidence:** ...
- **Evidence:** ...

(Repeat for each contrast.)

---

## 6. Open questions / validate with maintainers

Items where confidence is low but the question matters:

- <question, and why you couldn't infer confidently>
- <question>

Recommend raising these in an issue or draft PR before committing to a direction.

---

## 7. How this report should be used

- **Read-before-planning:** consult before drafting any non-trivial PR.
- **Validate, don't assume:** for substantial changes, verify the inferred norms with maintainers via issue or draft PR.
- **Not authority:** this report is a hypothesis set. Where it conflicts with reality, reality wins.
- **Do not show to maintainers as a "here's what we inferred about you" document.** It's contributor-facing preparation, not a conversation piece.

---

## 8. Re-run cadence

Archaeology reports decay. The project's practices shift; your sample becomes outdated.

- **Re-run after:** <trigger — e.g. after 3 months, or after N significant changes to the project's review culture>
- **Next planned re-run:** <date>

---

## 9. Ethical note

This report analyzes **decisions and norms**, not **personalities or motives**. Every claim about an individual is based on observable public artifacts and framed as an expectation the contributor should prepare for — not a psychological description.

If an entry in this report strays from that line, delete it.

---

## 10. Sources

List the artifacts analyzed, with links:

- PRs: #123, #456, #789, ...
- Issues: #234, #567, ...
- Release notes: vX.Y, vX.Z
- Design docs: `<path>`
- CONTRIBUTING: commit `<sha>`
