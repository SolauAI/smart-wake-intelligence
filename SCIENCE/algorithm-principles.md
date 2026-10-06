# Algorithm Principles

## Decision framing

For a configured interval `W = [floor, deadline]`, select a wake action only if it satisfies hard safety constraints and has adequate evidence of acceptable function. This is a constrained decision under uncertainty, not an optimization of “earliest alarm,” a score lookup or a sleep-cycle calculator.

`action(t) = wake at t`, for `t in W`; fallback is a deterministic alarm at `deadline`.

The candidate decision requires a conservative posterior/credible lower bound for acceptable function, not merely a high point estimate. Exact probability thresholds are deliberately unassigned until outcome data and false-early-wake harm weighting are validated.

## Separate latent state estimates

Keep the following estimates distinct and versioned. Each carries a range/distribution, evidence provenance and confidence—not a deceptive exact scalar.

1. **Sleep sufficiency:** protected personal opportunity range versus observed estimated opportunity; never equate low habitual duration with need.
2. **Recent recovery / sleep pressure:** recent short-night/recovery pattern and time-awake context; it is a proxy, not quantified debt in hours.
3. **Regularity:** deviation from the user’s established schedule distribution, interpreted as an association-aware longitudinal guardrail.
4. **Physiological stability:** baseline-relative, quality-gated HR/HRV/respiration/movement context; nonspecific and unable to decide alone.
5. **Circadian readiness:** timing proxy from schedule/local time/context, explicitly not measured biological phase unless validated instrumentation exists.
6. **Wake readiness / sleep inertia:** predicted short-term wake difficulty and functional state; an outcome target to validate, not an assumed capability.
7. **Stage estimate:** optional uncertain tie-breaker only after 1–6 and hard constraints pass.
8. **Decision confidence:** model/data support, missingness, staleness, disagreement, extrapolation and system health.

## Architecture: safety envelope + interpretable model

### Layer 0 — configuration and reliability
Validate time bounds, permissions, clock/time zone, supported device/version and a scheduled deadline fallback. If this fails, adaptive mode is unavailable.

### Layer 1 — non-negotiable safety envelope
Reject a candidate outside the window, in a low-confidence state, or when recent restriction/insufficient protected opportunity/critical data quality makes an earlier wake unacceptable. This layer cannot be bypassed by personalization.

### Layer 2 — feature construction
Build timestamped, quality-labelled feature ranges from current signals, multi-night history, context and baseline deviation. Do not impute missing physiology as normal; record missingness itself.

### Layer 3 — candidate prediction
At each supported candidate time, estimate outcome distributions for pre-specified endpoints: wake difficulty, next-day reaction-time result, daytime sleepiness/energy and regularity impact. Begin with transparent monotonic/regularized models and calibration checks. A hierarchical model may pool information while preserving individual uncertainty; it must not silently impose population thresholds as personal truth.

### Layer 4 — conservative selection
From candidates that pass Layer 1, choose the earliest one whose conservative evidence meets the policy. If none qualifies or confidence is inadequate, retain the deadline fallback. Stage may resolve a near-tie only if it cannot change a safety outcome.

### Layer 5 — audit and slow learning
Persist feature snapshot, versions, candidates, uncertainty, chosen action, fallback state, overrides and outcomes. Update only after delayed, quality-checked outcome data. Separate exploration from autonomous wake decisions; no unbounded or rapid sleep-shortening learning.

## Learning safeguards

- Establish a no-advancement baseline collection period.
- Use within-person comparisons with calendar/context controls and practice-adjusted cognitive tests where feasible.
- Treat missing feedback and overrides as informative but not proof of poor/good sleep.
- Monitor calibration separately across normal, travel, illness, alcohol, training and shift-like contexts.
- Version models and permit rollback; never overwrite historical decision context.
- A claim of improvement needs prospective out-of-sample evidence against fixed conservative alarms, not only retrospective fit.

## Explicit unknowns

The quantitative mapping from Garmin-derived data to “safe effective wake moment,” an acceptable probability threshold, minimum data history, and the incremental utility of staging remain unknown. These are feasibility/validation questions, not implementation assumptions.