# Biomarker Matrix

Every signal should be represented as value + timestamp + provenance + confidence + quality flags + deviation from personal baseline.

## High-value
Sleep timing: sleep onset, final awakening, time in bed, estimated total sleep time, awakenings. Primary role for sleep opportunity and regularity. Wearable detection is imperfect.

Longitudinal sleep duration: rolling 7/14/30/90-day distributions. Primary role for individual habitual sleep pattern and recent restriction.

Heart rate: overnight and resting trends. Supporting role for physiological deviation. Confounded by training, illness, alcohol, stress, temperature and other factors.

HRV: preferably RMSSD or equivalent when available. Supporting role for autonomic state relative to personal baseline. Never sole driver.

Respiration: overnight rate/trend. Supporting context; nonspecific.

## Medium-value
Movement: sleep/wake transition context and continuity. Quiet wake can resemble sleep.

Sleep stages: Garmin light/deep/REM estimates. Secondary or tie-breaker only because agreement with PSG is limited.

Body Battery: Garmin-specific trend/context only. Proprietary composite; do not map it directly to hours of sleep needed.

Stress: contextual physiological trend only; nonspecific.

## Forbidden deterministic rules
- 90-minute cycle arithmetic.
- "Deep sleep = X minutes, therefore wake now."
- "HRV below X = sleep longer by Y hours."
- "Body Battery below X = need Y additional hours."
- "Sleep score below X = delay alarm."

## Personal baseline
Maintain rolling central tendency, robust variability, recent trend, context tags, measurement quality and missingness.

Prefer within-person standardized deviations to population thresholds where justified.

## Confidence
Confidence falls with poor sensor contact, missing data, uncertain sleep onset/wake, strong signal disagreement, atypical nights or extrapolation beyond the learned range.

Low confidence must lead to conservative behavior, not aggressive sleep reduction.
