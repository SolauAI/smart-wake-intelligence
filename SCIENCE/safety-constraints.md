# Safety Constraints

1. User-defined latest wake time is absolute.
2. User-defined earliest safe wake time is respected.
3. No automatic shortening below a prudent floor without evidence and explicit policy.
4. Missing or unreliable sensing cannot trigger aggressive early waking.
5. Connectivity failure produces a deterministic fallback alarm.
6. The system must not claim medical certainty.
7. The system must not diagnose sleep disorders.

When uncertainty rises:
- widen the uncertainty interval;
- reduce reliance on weak signals;
- prefer the safer/later candidate inside the allowed window;
- preserve the hard latest-wake limit.

Repeated short nights should increase caution even if the user reports feeling normal.

Monitor rolling sleep duration, accumulated restriction, regularity, daytime impairment, physiological deviations and outcome trends.

Failure modes to test:
- Garmin fails to sync;
- watch battery dies;
- Bluetooth disconnects;
- phone is offline;
- sleep onset or wake is misdetected;
- stage estimate is wrong;
- HRV is missing/noisy;
- illness, training or stress creates unusual physiology;
- user changes schedule;
- user repeatedly overrides the model;
- subjective feedback remains positive while objective performance worsens.

Use "best estimate", "confidence" and "based on your recent sleep and signals". Avoid false precision such as "your body needs exactly 7h 42m".
