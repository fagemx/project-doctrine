# L3 — Methods (Acme SaaS)

## 3.1 — Plan round-2 review

**For:** Any plan that touches AI features or user-visible data paths.

**How:**
1. Plan author produces v1.
2. A second reviewer (human or agent) does a round-2 pass: blockers, missing pins, scope-fence violations.
3. Plan patches inline — round-2 corrections become visible as a section.
4. Only then execute.

**Why it works here:** Our AI features have coupling across prompt, citation, trust envelope, and kill-switch. A lone plan author consistently misses one of the four. Round-2 catches this.

**Concrete example:** Citation-in-response plan (2026-04-10). Round-2 surfaced that the plan didn't pin behavior when citation was absent — we would have shipped a UI that rendered "based on your data" with no source cell. Fixed pre-execution.

---

## 3.2 — Canary smoke against real vendor

**For:** Any AI feature path that talks to an external LLM provider.

**How:**
1. Canary suite runs every 6 hours AND on deploy.
2. Suite hits real vendor, real model, real API key.
3. On failure, page on-call AND flip feature flag to "off" automatically.
4. Post-incident: root-cause the vendor behavior; do not fix by mocking.

**Why it works here:** The 2026-04-08 incident (FM-2) cost us 6 hours of degradation because mocked CI tests passed while prod failed. Real-vendor canary was our root-cause fix.

**Concrete example:** 2026-04-15 vendor model version bump — canary detected a 3% spike in refusals within 12 minutes. Flagged; we contacted vendor; they confirmed rollback. Total user-visible degradation: zero.

---

## 3.3 — Kill-switch exercise during rollout

**For:** Any new feature-flagged feature.

**How:**
1. Enable flag in staging. Verify the "on" behavior.
2. Disable flag in staging under realistic load. Verify the "off" behavior is SAFE (no half-state, no cascade).
3. Only then flip the flag in production.

**Why it works here:** L1.4, L6.3. We learned that a kill-switch that has never been run cannot be trusted.

**Concrete example:** Citation-in-response (2026-04-15). During rollout we flipped the flag off mid-deploy. Found that turning it off also turned off the refusal path (shared dependency). Fixed the dependency before full rollout.

---

## 3.4 — User-correction telemetry as taste signal

**For:** Evaluating AI feature quality.

**How:**
1. Log every time a user corrects an AI output (edit, revert, re-ask with different phrasing).
2. Weekly review of top-corrected outputs.
3. If a class of correction recurs, it's a prompt / framing bug, not a user "getting used to it."

**Why it works here:** Benchmarks lie. Real user corrections are ground truth. We used to rely on vendor benchmarks; they told us our product was fine while users were frustrated.

**Concrete example:** March 2026 — benchmark score was stable but correction rate climbed. Investigation found the correction was always on confidence numbers. Led to L6.2 and FM-3.
