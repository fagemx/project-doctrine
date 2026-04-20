# Failure Memory — Acme SaaS

## FM-1: Auto-applied AI suggestions

**Temptation:**
"The model is confident, the user already asked for help, let's just apply the change and save them a click." It feels considerate. It looks like a better product demo.

**How it failed:**
- Model was wrong ~3% of the time
- Wrong suggestions applied to live customer data
- Undo existed but took 30+ seconds to navigate
- Users reverted via screenshots and manual re-entry (trust collapse)
- Rolled back the feature in 11 days

**Future detection:**
Any plan where an AI output causes a state mutation without an explicit user action between generation and commit.

**Correct move:**
Preview + confirm. Model output renders as a proposal. User clicks apply. The "saving a click" we thought we were giving users was an illusion; they wanted the click because it was their assertion of authority.

---

## FM-2: Mocked smoke tests

**Temptation:**
"Vendor API is slow / flaky / expensive; let's mock it in CI so tests are fast and deterministic."

**How it failed:**
- Mock returned 200 with fixture data even after vendor started refusing queries
- Regression undetected in CI for 4 days until a customer report
- 6 hours to full mitigation
- Lost trust with two enterprise accounts

**Future detection:**
Any PR that adds a mock in the request path to an external dependency whose behavior can change unilaterally (vendor APIs, LLM providers, third-party data sources).

**Correct move:**
Smoke suite runs against the real vendor on a canary schedule (every 6h + on deploy). Unit tests may mock; smoke must not.

---

## FM-3: AI confidence number without citation

**Temptation:**
"Users want to know how confident the AI is. Show the number." It looks like transparency.

**How it failed:**
- Users trusted the number more than their own judgment
- When the AI was wrong, users were confidently wrong
- "90% confident" and "I pulled this from row 42" feel different to users, but we only showed the first

**Future detection:**
Any UI proposal that surfaces a confidence / probability / certainty number without an accompanying source attribution.

**Correct move:**
Show the source. Skip the number. If citation is impossible, show a refusal ("I can't answer that from your data") instead of guessing.

---

## FM-4: Kill-switch that wasn't tested

**Temptation:**
"We have a kill-switch — it's a feature flag, we can flip it anytime." Feels safe because it *exists*.

**How it failed:**
- Flipping the flag also disabled the citation pipeline (shared upstream dependency)
- Which disabled the refusal path
- Cascade meant we had to flip *multiple* flags to restore a safe state
- Discovered at the worst possible moment (vendor incident in progress)

**Future detection:**
Any feature flag shipped without an exercise log showing the "off" state was tested under realistic load.

**Correct move:**
Rollout procedure includes flipping the flag off in staging under real load, verifying the resulting state is safe, then flipping it on.

---

## Starter traps (not yet seen but watch for)

- LLM output becoming dispatch tokens (callback IDs, URL paths, etc.)
- Adding rules to the prompt instead of reframing the task
- Making a scope-fence a guideline instead of enforcing it
- Assuming the model "understands" a constraint it was merely told
