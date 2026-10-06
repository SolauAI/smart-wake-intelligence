# iOS Architecture

## Verification status

Apple official URLs are listed in `RESEARCH/bibliography.md`. Direct current-documentation retrieval was blocked by the instruction to fetch all data only with GitHub CLI. Therefore the following is a conservative architecture specification; the exact iOS version, entitlement, notification/alarm API, permission and Focus/silent-mode behavior must be verified on supported physical devices before implementation claims.

## Hard design principle

The iPhone is the final alarm endpoint. It must hold a deterministic deadline fallback before sleep. The system must not depend on arbitrary continuous all-night processing, a live Garmin cloud feed, or a last-minute background execution opportunity.

## Required iOS state machine

1. **Unconfigured:** missing bounds, permission or supported configuration; adaptive mode unavailable.
2. **Armed:** user window validated; deadline fallback scheduled and persisted with an id/version.
3. **Monitoring best-effort:** optional Bluetooth/companion inputs are received; loss does not remove fallback.
4. **Adaptive candidate accepted:** candidate is inside bounds, safety layer passes, and the local alarm state is durably updated/acknowledged.
5. **Fallback:** deadline alarm remains authoritative when any health check/data/inference fails.
6. **Fired/acknowledged:** persist actual alarm time/path and collect outcome later.

Any transition failure resolves toward `Fallback`, never toward an earlier alarm or an unarmed state.

## Official-API verification checklist

On every supported iOS release/device, verify from Apple documentation and instrumented test:

- local-notification/alarm scheduling limits, persistence, audible sound rules and maximum sound behavior;
- availability, entitlement, review conditions and semantics of any alarm- or critical-alert mechanism considered;
- notification authorization, Focus, silent mode, device-lock and user-settings effects;
- Core Bluetooth state restoration/background limits and what is actually guaranteed versus opportunistic;
- BackgroundTasks scheduling/launch guarantees (not a wake-deadline scheduler);
- app force-quit, crash, reboot, low-power mode, time-zone/DST and clock-change behavior;
- reschedule/cancel race conditions and whether deadline fallback can be accidentally cleared.

## Reliability requirements

- Persist the complete armed state atomically before sleep confirmation.
- Schedule and read back the fallback alarm at arm time; show clear degradation if confirmation is impossible.
- All incoming watch events are optional, authenticated/validated, ordered/freshness-checked and idempotent.
- Use a watchdog/audit record for every arming, modification, fallback and fire event.
- Test physical audible delivery; an API call succeeding is not evidence that the user heard an alarm.

## Product boundary

V1 may need to state a narrow supported iPhone/iOS/permission configuration. If iOS cannot supply verified audible reliability for the needed alarm behaviour, the product must remain shadow/decision-support mode rather than promise an adaptive alarm.