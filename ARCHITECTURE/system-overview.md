# System Overview

## Target architecture

Garmin wearable
    |
    | sensing / derived features
    v
Night decision engine
    |
    | wake event
    v
iPhone companion
    |
    v
Reliable local alarm

## Responsibilities

### Garmin layer
Collect available physiological/activity information and, where technically feasible, perform low-latency feature extraction.

### Decision engine
Maintain personal baselines, estimate sufficiency/recovery/readiness, enforce safety constraints and select a candidate wake time.

### iPhone
Own the user-facing configuration, persistence, alarm endpoint and feedback loop.

## Architecture priority
Reliability > safety > scientific validity > optimization > complexity.

## Two-track feasibility plan
Track A: direct Garmin/Connect IQ plus iPhone companion.
Track B: Garmin Health SDK where licensing and real-time data access make it appropriate.

The final V1 architecture must be selected only after testing the exact Garmin model intended for launch.
