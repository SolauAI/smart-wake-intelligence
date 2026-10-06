# Safety Constraints

## Safety invariant

The system is a wellness decision-support/alarm product, not a medical device or sleep-disorder diagnostic. Its optimization target is **minimum safe effective sleep**, not earliest waking. Alarm reliability outranks adaptation.

## Hard constraints for every night

1. The user supplies an earliest permissible wake time (`floor`) and hard latest wake time (`deadline`), with `floor <= deadline`.
2. The system must have a deterministic iPhone fallback alarm at the deadline before adaptive mode is considered active.
3. An adaptive alarm may sound only within `[floor, deadline]`. It may never advance earlier than the floor or delay past the deadline.
4. A missing sensor, lost Bluetooth connection, delayed data, app suspension/relaunch, inference error or low confidence must not cause early waking. It resolves to a conservative scheduled alarm within the window, normally the deadline.
5. The user can view fallback/adaptive state and manually override the selected time.
6. No single HRV value, HR value, Body Battery, sleep score or estimated sleep stage can trigger or veto waking by itself.
7. No 90-minute-cycle arithmetic is permitted.
8. The model may not reduce its estimated required opportunity merely because subjective ratings are positive. Objective/behavioural outcomes and multi-night safety evidence are required.

## Conservative mode triggers

Use fallback/conservative behaviour if: baseline history is inadequate; the current night lies outside learned support; sensing quality is poor; data are stale; clock/permission/alarm scheduling state is unknown; illness/alcohol/travel/unusual training is reported or inferred; recent restriction/irregularity is elevated; or any critical component has not passed health checks.

## Longitudinal stop / rollback criteria

Adaptive advancement is suspended and a fixed conservative schedule is restored if pre-specified monitoring finds: repeated short opportunities versus the protected baseline; worsening reaction-time trend after practice adjustment; sustained daytime sleepiness/functional impairment; degraded regularity; high override rate; alarm-delivery failure; or significant unexplained physiological deviation. These are product safety triggers, not diagnoses.

## Required failure-mode tests

| Failure | Required behaviour | Test evidence |
|---|---|---|
| Watch battery depletion/off-wrist | Deadline fallback remains armed. | Instrumented overnight simulation and device test. |
| Bluetooth disconnect / phone offline | No dependency on a late cloud sync; fallback stays armed. | Fault injection before/during wake window. |
| Garmin message/data delayed or malformed | Reject stale/invalid event; preserve scheduled fallback. | Schema/version/staleness tests. |
| App terminated/relaunched | Persist state and reconcile safely; do not lose deadline alarm. | Lifecycle test matrix on supported iOS versions. |
| Notification/permission/focus/silent condition | Detect unsupported state before sleep and communicate failure; verify audible delivery in supported configuration. | On-device reliability test; no unsupported promise. |
| Clock/time-zone change | Recompute bounds in a documented time-zone policy; never alarm outside explicit bounds. | Time-zone/DST simulations. |
| Model exception/timeout | Fail closed to conservative alarm and durable reason code. | Forced-exception test. |
| Misclassified stage / noisy HRV | Cannot outweigh hard constraints or core multi-night evidence. | Adversarial replay. |

## Communication constraints

Use “estimate,” “confidence,” “based on recent signals,” and exact fallback status. Do not say “your body needs exactly X,” “recovered,” “safe,” “deep sleep,” or “perfect wake moment” without qualification. Escalate user-reported dangerous sleepiness or suspected disorder to appropriate professional advice rather than an algorithmic adjustment.