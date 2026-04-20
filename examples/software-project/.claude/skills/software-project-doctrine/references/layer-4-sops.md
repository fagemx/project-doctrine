# L4 — SOPs (Acme SaaS)

## SOP-1: Vendor LLM degradation suspected

**Triggered when:** Canary alerts fire, or a user reports AI behavior regression, or the vendor posts an incident notice.

**Steps:**
1. Acknowledge alert. Set on-call status.
2. Check canary history — is this a step-change or drift?
3. If step-change: flip kill-switch per SOP-3. Post in `#incidents`.
4. Hit vendor status page. Open a support ticket if not already acknowledged.
5. User comms: the pre-written template in `docs/runbooks/ai-degradation-comms.md`.
6. Monitor canary recovery. Re-enable on two consecutive green runs + vendor all-clear.
7. Write the incident retro within 48h. Update L6 if a new scar emerged.

**Done when:** Canary green, user comms sent, retro filed.

**Common failure mode:** Skipping step 5 (user comms). Users learning of the degradation from their own workflow before we tell them costs more trust than the degradation itself.

---

## SOP-2: New AI feature proposal

**Triggered when:** A PM or engineer proposes adding a new AI-driven capability.

**Steps:**
1. Write a plan doc. Include: what the AI produces, what's citable, what the refusal path is, what the kill-switch looks like.
2. Run round-2 review (SOP-4).
3. Build behind a flag.
4. Exercise kill-switch (L3.3).
5. Canary smoke (L3.2).
6. Rollout: 5% → 25% → 50% → 100%, gated on correction-rate telemetry (L3.4).
7. Retire old equivalent if applicable.

**Done when:** Feature at 100% for ≥2 weeks with correction-rate ≤ baseline.

**Common failure mode:** Skipping the refusal-path definition in step 1, discovering in rollout that the feature has no graceful "I don't know" state.

---

## SOP-3: Flip kill-switch in production

**Triggered when:** Canary alert or incident response calls for disabling an AI feature.

**Steps:**
1. Verify the flag name and current state.
2. In staging, flip the flag — verify "off" behavior.
3. In production, flip the flag. Confirm via live traffic check.
4. Post in `#incidents`: `flag X flipped at HH:MM UTC by @who, reason: <short>`.
5. Monitor user-facing error rate for 10 minutes.

**Done when:** Flag flipped, comms posted, error rate stable.

**Common failure mode:** Skipping step 2 (staging verify). Last time someone skipped it, the flag cascade took the citation pipeline with it (FM-4, L6.3).

---

## SOP-4: Plan round-2 review

**Triggered when:** A plan is proposed for any non-trivial work.

**Steps:**
1. Author submits plan v1 with explicit Implementation Pins.
2. Reviewer reads and produces a `## Round-2 Corrections` section with: (a) blockers, (b) missing pins, (c) scope-fence drift.
3. Author patches v1 inline; round-2 section stays visible as an artifact.
4. Re-review only if blockers remain.
5. Green-light → execution.

**Done when:** All round-2 blockers closed and author has green-lit the plan.

**Common failure mode:** Author treating round-2 as suggestions rather than blockers. Round-2 is a gate, not feedback.

---

## SOP-5: AI feature correction spike

**Triggered when:** Weekly correction-rate review (L3.4) shows a feature's correction rate is 2x its rolling baseline.

**Steps:**
1. Pull the top 20 corrected outputs for that feature.
2. Categorize: (a) hallucination, (b) confidence miscalibration, (c) framing error, (d) user expectation drift.
3. For (a/b/c): write a plan to fix. Do NOT add prompt rules as the first move (L6.5 — framing > model capacity).
4. For (d): possibly not a bug; may be a product-messaging update.
5. If correction rate stays elevated for 2 consecutive weeks, consider flipping the feature off while fixing.

**Done when:** Plan written AND correction rate returned to baseline ± 20%.

**Common failure mode:** Responding to (c) framing errors by stacking more rules in the prompt. L6.5 says first ask if the frame is wrong, not if the prompt needs more rules.
