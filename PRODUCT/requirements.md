# Product Requirements

## Product objective

Within a user-defined window, choose the earliest **sufficiently supported** wake moment while protecting long-term sleep opportunity, recovery and regularity. The product must be willing to choose the hard latest time when uncertainty or safety requires it.

## P0 — safety and reliability (must precede adaptive control)

- User-configured earliest permissible wake time and hard latest wake time; validation and clear time-zone/DST behavior.
- Persisted, verified iPhone deadline fallback alarm before sleep.
- Clear state: armed, adaptive available, degraded/fallback and reason.
- No out-of-window adaptive decision; no alarm state that silently loses the deadline fallback.
- Garmin/phone data provenance, freshness, quality, missingness and version capture.
- Multi-night history for estimated opportunity, recent restriction and regularity; label uncertainty explicitly.
- Auditable decision record with policy/model/input versions and override path.
- Manual override and user-visible selected/fallback time.
- Strict prohibition of 90-minute-cycle logic and single-metric decisions.
- Privacy/data-minimization and user control over sensing/outcome collection.

## P1 — research-mode outcomes and validation support

- Morning wake-difficulty and sleep-quality measures, designed to minimize burden.
- Optional standardized short reaction-time task with practice tracking and protocol checks.
- Daytime sleepiness/energy/functional outcome capture.
- Context tags: illness, alcohol, unusual training, travel, shift-like schedule, medication change (optional; not diagnostic).
- Historical explanation separating observations, estimates, uncertainty and decision constraints.
- Calibration/safety monitoring dashboard for research operations, including overrides, degradation and alarm delivery.

## P2 — only after P0/P1 evidence gates

- Conservatively adaptive alarm in a limited supported configuration.
- Optional wake-light integration, clearly described as an alerting aid—not recovered-sleep evidence.
- Additional wearables only after device-specific validation.
- More complex models only if prospective out-of-sample benefit, calibration and auditability beat simpler models.

## Non-functional acceptance criteria

- **Reliability:** no claim of alarm reliability absent on-device fault-injection evidence for every supported configuration.
- **Safety:** any degraded data/system state has a deterministic fallback that respects the deadline.
- **Scientific integrity:** user copy distinguishes wearable estimates, hypotheses and validated outcomes; never promises a perfect sleep cycle/precise sleep need.
- **Explainability:** every automated decision has human-readable reason codes and reconstructable inputs.
- **Evaluation:** promotion requires pre-specified safety/function outcomes, not “minutes gained.”

## Explicit non-requirements for V1

No diagnosis; no precise circadian-phase claim; no equivalence to PSG; no guarantee Garmin cloud is real-time; no continuous all-night iPhone processing assumption; no automatic inference that positive self-report permits less sleep.