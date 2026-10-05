# User Flow

## Setup
1. User installs app.
2. Connects supported Garmin.
3. Grants required permissions.
4. Sets earliest and latest wake times.
5. Chooses whether to provide morning feedback.
6. Completes baseline period without aggressive adaptive shortening.

## Night
1. User starts sleep mode.
2. Garmin remains on wrist.
3. System collects and evaluates signals.
4. Model updates candidate wake times.
5. Safety layer constrains the result.
6. iPhone holds the alarm/fallback state.

## Morning
1. Alarm sounds.
2. User stops alarm away from bed.
3. App asks for a very short wake-quality rating.
4. Optional reaction-time test.
5. App stores outcomes.

## Longitudinal loop
Data -> baseline -> prediction -> decision -> outcome -> calibration.

The user should never need to understand the underlying biomarkers to benefit from the product.
