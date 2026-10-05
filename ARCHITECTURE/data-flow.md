# Data Flow

1. User configures wake window.
2. User sleeps with Garmin on wrist and iPhone away from bed.
3. Garmin collects available signals.
4. Night engine derives features and confidence.
5. Candidate wake moments are evaluated within the allowed window.
6. Earliest candidate satisfying safety policy is selected.
7. iPhone receives/uses the wake decision.
8. iPhone sounds the alarm.
9. User provides morning outcome.
10. Optional daytime cognitive/energy outcome is collected.
11. Longitudinal state is updated.

## Signal object
Each signal includes:
- metric;
- value;
- unit;
- timestamp/interval;
- source device;
- source layer;
- quality;
- confidence;
- personal-baseline deviation;
- missingness flag.

## Decision record
Persist earliest wake, latest wake, sleep-onset estimate, actual decision, candidate times, feature snapshot, confidence, reason codes, fallback state, override and next-day outcomes.

## Offline evaluation
Replay historical nights and compare against fixed 7 h, 8 h, 9 h, the user's existing alarm and a conservative latest-bound policy.

Evaluate safety and next-day outcomes, not just alarm earliness.
