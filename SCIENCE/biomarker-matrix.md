# Biomarker Matrix

Every feature is stored as: value, unit, interval/timestamp, source/device/firmware, acquisition layer, quality flags, missingness, baseline reference, deviation estimate and uncertainty. No unqualified scalar is a decision input.

| Domain / signal | Evidence status and role | Main confounding / uncertainty | Allowed use | Prohibited use |
|---|---|---|---|---|
| Sleep opportunity: bedtime, estimated onset, final wake, time in bed, estimated total sleep time | A/B. Core evidence for opportunity and recent restriction, but wearable estimates are imperfect. | Quiet wake, missing wear, sleep-onset error, device algorithm changes. | Estimate a range for sleep opportunity; update longitudinal history. | Treat a single-night estimate as exact sleep obtained/needed. |
| Multi-night duration distribution and short-night count | B. Core safety context. | Personal baseline may reflect chronic restriction; missing nights and schedule changes. | Track robust rolling distributions, trend and uncertainty. | Learn that low habitual duration equals low biological need. |
| Regularity: timing/duration variability | B association evidence. | Shift work, travel, intentional schedule changes, reverse causality. | Longitudinal guardrail and evaluation outcome. | Claim causal health improvement from a one-night schedule choice. |
| HR / resting HR trend | B supporting physiology. | Training, fever/illness, alcohol, medication, stress, temperature, sensor contact. | Contextual baseline-relative deviation. | Single threshold or independent wake decision. |
| HRV (metric and measurement conditions explicit) | B supporting physiology. | Same as HR plus posture, breathing, sampling/algorithm changes and artefact. | Contextual evidence when quality is adequate. | Convert to “hours of sleep debt” or a direct wake-time rule. |
| Respiratory-rate trend | B/C nonspecific context. | Illness, altitude, device error, medication, environment. | Flag atypical physiology and reduce confidence. | Diagnose disease or infer recovery alone. |
| Movement / actigraphy-like data | B transition/continuity context. | Quiet wake resembles sleep; restless sleep is nonspecific. | Assist sleep-wake estimates and signal-quality checks. | Declare sleep stage or safe wake minute. |
| Consumer sleep stage | C for this use case. Indirect, device-specific estimate. | Limited PSG agreement, unknown current firmware performance, classification delay. | Optional confidence-gated tie-breaker between candidates that already pass safety. | Override sufficiency/restriction/regularity, use deep/light/REM deterministic rule, 90-minute rule. |
| Garmin Body Battery, stress, sleep score | C/D proprietary composite. | Opaque algorithm, version drift, overlap with component inputs. | Display/context only if provenance/version is logged. | Use as a physiological truth or independent decision driver. |
| Circadian proxies: habitual midpoint, schedule, local time, light/context when available | B/C. Timing matters; proxy phase is uncertain. | Travel, shift work, light exposure, chronotype, missing context. | Penalize implausible schedule shifts; stratify validation. | Claim measured circadian phase without validated measurement. |
| Morning wake difficulty / sleep quality | B outcome; subjective but important. | Expectancy, reporting fatigue, adaptation. | Calibrate user experience paired with other outcomes. | Alone establish safety or reduced sleep need. |
| Daytime sleepiness/energy | B outcome/supporting signal. | Reporting bias, caffeine, workload, mood, illness. | Longitudinal outcome and safety monitoring. | Treat as objective recovery proof. |
| Short reaction-time test | B feasible functional outcome if protocol adherence is known. | Practice effects, phone/device latency, motivation, time of day. | Pre-specified within-person outcome with practice-adjustment/control. | Diagnostic cognitive assessment or sole criterion. |
| Training/recovery context | C/B contextual outcome. | Training-load measurement error, selection bias, sport specificity. | Stratify/adjust evaluation; reduce confidence in atypical physiology. | Infer sleep need from one training response. |

## Confidence policy

Confidence declines with missing or delayed data, poor contact, discordant signals, unmodelled context, drift outside prior observations, insufficient baseline history or a vendor/app version change. Low confidence can only remove an earlier option; it cannot justify an earlier alarm.

## Baseline policy

Baselines are robust, context-stratified and versioned. A baseline built during repeated short sleep is labelled potentially constrained, not “true sleep need.” Population cutoffs are never silently substituted for a personal estimate.