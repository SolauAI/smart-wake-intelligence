# Data Flow

## Safety-first flow

1. User supplies local-time `floor` and `deadline`; the phone validates bounds, time-zone policy and supported configuration.
2. iPhone persists and verifies a deterministic deadline fallback alarm before the night begins.
3. Garmin/approved companion produces best-effort observations or compact features, each with source/device/firmware, interval, timestamp, freshness, quality and schema version.
4. Ingestion validates, deduplicates and labels missing/stale/inconsistent data. It does not assume normality for missing data.
5. Night engine updates separate uncertainty-aware state estimates: sufficiency, recent restriction/recovery, regularity, physiological stability, circadian proxy and wake readiness.
6. Candidate times inside the window are assessed by the safety envelope then the interpretable outcome model. Stage is optional secondary evidence only.
7. If a candidate is accepted, phone atomically updates the local alarm state while retaining/replacing the deadline fallback only after durable acknowledgement.
8. If no candidate qualifies or any component is unhealthy, phone retains deadline fallback.
9. On alarm fire, persist selected/actual time, path (adaptive/fallback), system health and reason codes.
10. Collect delayed morning/daytime outcomes; update longitudinal model only after quality checks.

## Signal object

```text
signal = {
  id, metric, value, unit, interval_start, interval_end,
  received_at, monotonic_timestamp, source_layer, device_model,
  firmware, vendor_algorithm_version?, quality_flags, missingness,
  freshness, baseline_reference_version, deviation_distribution,
  uncertainty, schema_version
}
```

## Decision record

```text
decision = {
  decision_id, created_at, time_zone, floor, deadline,
  fallback_alarm_id, candidate_times, accepted_time?, actual_fire_time?,
  path: adaptive|fallback|manual_override, constraint_results,
  state_estimates_with_intervals, input_provenance, data_freshness,
  model_version, policy_version, confidence, reason_codes,
  system_health, user_override, outcome_links
}
```

## Boundary and privacy rules

- Raw data are minimized; features/outcomes are retained only with purpose, provenance and retention policy.
- Data generated after a decision cannot alter the historical record; append corrections/version links instead.
- Clock/time-zone conversion is centralized and testable; every decision stores the resolved local zone.
- Cloud synchronization is asynchronous and must not be required for the deadline fallback.
- Model training consumes de-identified/versioned datasets only where consent and data governance allow.

## Offline evaluation

Replay historical nights without leaking future information. Compare: user’s existing alarm; fixed conservative schedule; fixed-duration schedules; safety-envelope-only fallback; and personalized candidate model. Assess pre-specified safety/function outcomes, calibration, regularity, alarm delivery and subgroup/context failures—not merely average earliness.