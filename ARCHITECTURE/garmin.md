# Garmin Architecture

## Verification status

Official-source URLs are in `RESEARCH/bibliography.md`, but the GitHub-CLI-only acquisition constraint prevented direct reading of the current Garmin contracts in this pass. Statements labelled **to verify** are design hypotheses/gates, not facts suitable for implementation.

## Candidate integration tracks

### Track A — Garmin Health API (post-sync / cloud)

Repository source: Garmin Health API. **To verify:** commercial eligibility/licensing, data scopes, retention, latency, supported metrics/models, webhook/poll semantics and whether data are available soon enough for a wake decision.

Design consequence: do not assume cloud data have real-time latency. This track is potentially suitable for longitudinal history and retrospective analysis, not a relied-on last-minute alarm path until latency is measured on target devices.

### Track B — Garmin Health SDK (licensed direct/real-time option)

Repository source: Garmin Health SDK. **To verify:** commercial contract, iOS compatibility, actual signal set, sampling/latency, background behavior, model list and failure semantics.

Design consequence: this is a feasibility gate; do not architect against undocumented streaming guarantees.

### Track C — Connect IQ watch app + phone companion

Repository sources: Connect IQ `Toybox.Communications`, backgrounding and `ServiceDelegate`. **To verify on exact model/firmware:** which overnight signals are exposed to Connect IQ; whether background services are scheduled/terminated; transport wake-up/delivery behavior; resource limits; and iOS companion interoperability.

Design consequence: compact, timestamped events/features are preferred to raw continuous data. Watch-side execution cannot be assumed to persist or deliver at the desired moment.

## Prohibited assumptions

- Garmin Connect cloud data are real-time enough for an alarm.
- Garmin sleep stages are PSG or available with useful immediate latency.
- A Garmin proprietary score is a validated wake-readiness signal.
- A watch-to-phone event will always arrive at the deadline.
- One Garmin model/firmware result generalizes to all Garmin devices.

## Night protocol (only after feasibility proof)

1. Before sleep, iPhone validates pairing/support state and schedules its own deadline fallback.
2. Garmin/companion emits only schema-versioned events with device, firmware, monotonic and wall-clock timestamps, freshness, quality and sequence identifiers.
3. iPhone rejects stale, duplicated, malformed or unsupported events.
4. A decision event can propose a candidate inside the user’s window but cannot cancel the deadline fallback until the phone has durably acknowledged the selected alarm state.
5. Disconnect or degraded quality moves the system to conservative fallback; it never produces an earlier wake.

## Required feasibility matrix before V1 selection

For every target watch, firmware and iPhone/iOS combination, measure: signal availability; event latency distribution; overnight battery effect; disconnect/reconnect behavior; transport reliability through the configured wake window; behavior after phone/watch app termination; data schema/version drift; and alarm outcome under fault injection. Publish pass criteria before collecting adaptive effectiveness data.

## Data boundary

Collect only signals justified by a documented research question. Store source layer and vendor/device/firmware metadata to make algorithm drift detectable. Garmin-derived data are estimates, not clinical measurements.