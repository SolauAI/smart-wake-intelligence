# Roadmap

## Phase 0 — R&D foundation
- Consolidate primary evidence.
- Verify Garmin integration options.
- Verify current iOS alarm/background constraints.
- Define data schema.
- Define safety policy.
- Define offline validation protocol.

## Phase 1 — Data collection prototype
- Connect one target Garmin model.
- Capture nightly data.
- Build personal baseline engine.
- Build decision-log pipeline.
- No autonomous sleep shortening yet.

## Phase 2 — Retrospective validation
Replay historical nights and compare fixed-duration alarms, conservative rules and personalized probabilistic models.

Primary evaluation: next-day outcomes and safety.
Secondary evaluation: unnecessary time in bed preserved / alarm earliness.

## Phase 3 — Shadow mode
Model generates recommendations but does not control the alarm. Compare with actual alarm, morning feedback and daytime outcomes.

## Phase 4 — Guarded adaptive alarm
Enable autonomous adaptive waking only inside strict bounds with deterministic fallback. Start conservatively.

## Phase 5 — Personalization
Use longitudinal outcomes to calibrate the user's sleep-response model. Require demonstrated improvement over simpler baselines.

## Phase 6 — Productization
Reliability hardening, privacy/security, onboarding, UX, device compatibility, monitoring and App Store requirements.

## Success criteria
The system succeeds only if out-of-sample evaluation shows that adaptive waking:
1. does not increase harmful sleep restriction;
2. preserves or improves next-day function;
3. reduces unnecessary time in bed for appropriate users;
4. maintains acceptable schedule regularity;
5. remains reliable when sensors/connectivity fail.
