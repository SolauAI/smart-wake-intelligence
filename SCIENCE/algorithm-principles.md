# Algorithm Principles

## Objective
For a user-defined wake window [earliest, latest], estimate for each candidate wake time t:

P(wake at t is sufficiently restorative and acceptable | current night, recent history, personal model, context)

Choose the earliest candidate whose posterior probability and safety constraints satisfy product policy.

This is a probabilistic decision problem, not a sleep-score lookup.

## Latent dimensions
Maintain separate estimates of:
1. Sleep Sufficiency
2. Recent Recovery / Sleep Pressure
3. Physiological Stability
4. Circadian Readiness
5. Wake Readiness
6. Uncertainty / Confidence

Do not collapse them prematurely into one opaque score.

## Decision logic
1. Establish hard bounds.
2. Estimate current sleep opportunity and recent history.
3. Update personal baseline deviations.
4. Estimate candidate wake readiness over the allowed window.
5. Use stage information only as a secondary signal.
6. Calculate confidence.
7. Select earliest candidate meeting safety criteria.
8. If confidence is inadequate, use conservative fallback behavior.
9. Log the decision and inputs.
10. Collect outcomes and update slowly.

## Learning
Learn individual sleep-duration distribution, response to restriction, relationship between physiology and next-day function, wake difficulty and regularity.

Do not learn from subjective comfort alone. Pair subjective feedback with objective or behavioral outcomes when possible.

## Validation
Primary endpoints: reaction time / cognitive performance, wake difficulty, daytime sleepiness, functional energy, adherence to intended schedule.

Safety endpoints: repeated restriction, increasing sleep debt, worsening regularity, sustained physiological deterioration and persistent daytime impairment.

## Model evolution
1. Rule-based safety layer.
2. Interpretable probabilistic model.
3. Personalized hierarchical model.
4. More complex ML only if it improves out-of-sample outcomes and remains auditable.

Never optimize directly for "earliest alarm". Optimize safe functioning and long-term outcomes.
