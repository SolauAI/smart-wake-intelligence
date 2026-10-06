# Roadmap

## Gate 0 — source and feasibility closure (current; no production implementation)

- Complete primary-source reconciliation for every evidence-registry claim: source, population, design, outcome, limitations and implication.
- Read/version/date official Garmin and Apple documentation outside this GitHub-CLI-only evidence constraint, or explicitly lift that constraint for source verification.
- Select candidate Garmin models and iPhone/iOS support matrix.
- Write quantitative pass/fail criteria for signal availability, event latency, iPhone alarm delivery and fallback reliability.
- Freeze safety policy, time-zone policy, data schema and decision-record specification.

**Exit:** auditable bibliography; vendor-contract matrix; unresolved questions explicitly retained; no unsupported claims.

## Gate 1 — hardware/software feasibility prototype (not adaptive)

- Test exact watch/firmware/phone/iOS combinations with instrumented overnight and fault-injection runs.
- Demonstrate deadline fallback survives supported disconnect, stale-data, app lifecycle, clock/time-zone and low-quality-input scenarios.
- Measure—not assume—Garmin signal availability/latency and phone alarm delivery.
- Build only data capture, health checks, audit logging and fixed fallback behaviour.

**Exit:** measured support matrix and demonstrated fallback reliability. Failure keeps product in data-collection/decision-support mode.

## Gate 2 — observational baseline and protocol calibration

- Collect a no-advancement baseline with sleep/opportunity history, regularity, wake difficulty, daytime outcomes and optional reaction-time protocol.
- Pre-register endpoints, missing-data handling, exclusion rules, stopping/rollback criteria and false-early-wake cost.
- Establish robust within-person baselines; mark chronically restricted-looking baselines as uncertain.

**Exit:** adequate data quality/history definition and a locked offline-analysis plan.

## Gate 3 — retrospective validation

- Perform temporal holdout replay with no future-data leakage.
- Compare existing alarm, fixed conservative schedule, deadline fallback, safety-envelope-only policy and proposed personalized model.
- Evaluate calibration, safety events, functional outcomes, regularity and context/subgroup degradation; earliness is secondary.

**Exit:** model exceeds simple baselines on pre-specified safety/function criteria without increasing restriction. Otherwise simplify or stop.

## Gate 4 — prospective shadow mode

- Generate recommendation only; user’s actual alarm remains conservative/fixed.
- Measure prediction calibration, counterfactual limitations, alarm logistics and outcome burden.
- Exercise rollback and all failure paths continuously.

**Exit:** prospective evidence that the model remains calibrated, useful and operationally reliable; ethics/privacy review is complete.

## Gate 5 — guarded adaptive pilot

- Enable only inside strict bounds and selected supported configurations.
- Start with conservative advancement limits defined by evidence—not a product growth target.
- Monitor override rate, short-night trend, regularity, reaction-time/daytime outcomes, fallback usage and alarm failures.
- Automatic rollback to fixed conservative fallback on stop criteria.

**Exit:** independently reviewed evidence of non-inferior safety/function and acceptable reliability versus fixed conservative alarm.

## Gate 6 — productization

- Security/privacy/data-governance hardening, usability research, support playbooks, device compatibility governance and longitudinal post-release monitoring.
- Version and communicate every material model/vendor-algorithm change.

## Core success criteria

A system is successful only if prospective, out-of-sample evidence shows it: (1) does not increase harmful restriction; (2) preserves or improves predefined next-day function; (3) does not degrade regularity; (4) delivers reliable alarms under supported fault cases; and (5) communicates uncertainty without false medical precision. “Waking earlier” alone is not success.