# Evidence Registry

## Research-access status — 2026-10-06

This repository was fetched from GitHub with `gh`. The user required GitHub CLI for all data acquisition. GitHub CLI cannot retrieve PubMed full text, Garmin Developer documentation, or Apple Developer documentation; therefore this pass **does not claim independent current-source verification beyond the source URLs already stored in the repository**. Exact bibliographic metadata and current vendor contracts below are a reconciliation target, not a substitute for reading the primary paper or official contract. No production implementation is authorized from this registry.

## Evidence levels

- **A — established:** replicated experimental evidence or authoritative consensus directly supports the narrowly worded claim.
- **B — supported but limited:** credible evidence, but population, setting, outcome or external validity limits the product conclusion.
- **C — hypothesis:** reasonable mechanism/product hypothesis; it must not determine alarm time without prospective validation.
- **D — unknown:** no adequate evidence for the intended decision.

## Claims and reconciliation

| ID | Claim and level | Source; population/design/outcome | Limitations | Practical implication |
|---|---|---|---|---|
| E1 | **A:** Adults generally need at least 7 h regular sleep opportunity; individual need varies. | Watson et al., 2015, AASM/SRS consensus; expert review/consensus, not an individual prediction study. Recommendation: adults 18–60 should sleep >=7 h regularly. https://doi.org/10.5664/jcsm.4758 | Population guidance is not a personal lower bound, recovery prescription, or alarm rule. | Never optimize toward 7 h or infer a user is safe to shorten because they exceed it. |
| E2 | **A:** Chronic partial restriction produces cumulative objective neurobehavioral impairment, while subjective sleepiness may not track it. | Van Dongen et al., 2003; healthy adults, controlled 14-day dose-response (4/6/8 h time-in-bed) plus 9 h control; psychomotor vigilance and cognitive outcomes worsened dose-dependently. https://doi.org/10.1093/sleep/26.2.117 | Laboratory schedule and healthy sample; time in bed is not sleep duration; does not define individual sleep need. | Do not learn a shorter need from self-report alone; use multi-night history and feasible objective outcomes. |
| E3 | **B:** Vulnerability to sleep loss differs consistently between people. | Van Dongen et al., 2004; controlled repeated sleep-loss observations; individual differences in neurobehavioral impairment appeared trait-like. https://doi.org/10.1093/sleep/27.3.423 | Does not establish that a consumer wearable can identify a resilient person or safe short sleep. | Use within-person calibration; start conservative and retain uncertainty. |
| E4 | **B:** One or two recovery nights may not normalize all effects of prior restriction. | Belenky et al., 2003; controlled sleep-dose/recovery study in healthy adults; performance recovery depended on prior restriction. https://doi.org/10.1046/j.1365-2869.2003.00337.x | Protocol-specific; not a formula for “sleep debt” or recovery hours. | Preserve a separate recent-restriction state; a good current night cannot erase history. |
| E5 | **B:** Greater schedule regularity is associated with better health/sleep-related outcomes. | Phillips et al., 2017; observational cohort; sleep regularity index associated with outcomes. https://doi.org/10.1038/s41598-017-03171-4 | Association, residual confounding, no proof that an alarm-caused shift changes health. | Regularity is a longitudinal guardrail/supporting objective, not a causal health score. |
| E6 | **A/B:** Sleep/wake regulation reflects interacting homeostatic and circadian processes. | Borbély, 1982; theoretical/physiological two-process model. PMID 7185792. | Model is not a consumer-level circadian-phase sensor and cannot yield minute-level wake readiness. | Model sleep opportunity/recent restriction separately from timing/circadian proxies. |
| E7 | **B:** Sleep inertia exists and is shaped by sleep stage, circadian time, prior sleep loss and awakening conditions. | Tassi & Muzet, 2000; review of experimental evidence. https://doi.org/10.1053/smrv.2000.0098 | A review; stage-specific effect sizes and consumer-device application remain uncertain. | Treat wake readiness as an outcome to validate; stage can only be a low-weight tie-breaker. |
| E8 | **B:** Consumer wearables are imperfect versus PSG, especially for wake and stage classification. | de Zambotti et al., 2019; review. https://doi.org/10.1016/j.smrv.2019.101212. Repository also cites PubMed 39484805, 40303381 and 38557808; exact study metadata/full text remains to be checked. | Accuracy varies by device, firmware, population and epoch; review is not Garmin-model validation. | Store quality/missingness/provenance; never equate Garmin staging with EEG/PSG. |
| E9 | **B:** Autonomic measures change with sleep loss, but HR/HRV are nonspecific. | Repository source: PubMed 40895095 (reported sleep-deprivation HRV meta-analysis); PubMed 33897355 (wearable restriction study). | Exact metadata and primary-study details require source check; HRV is affected by illness, alcohol, training, medication, stress and measurement conditions. | Use HR/HRV only as baseline-relative contextual evidence; never as a single alarm trigger. |
| E10 | **B/C:** Light timing/characteristics can affect alertness. | Repository source: PubMed 35142669 (reported meta-analysis). | Alertness improvement is not proof of recovered sleep need; intervention/device dose matters. | Future wake-light support must not justify earlier waking. |
| E11 | **C:** Stage-aware smart alarms improve real-world next-day outcomes. | Repository source: PubMed 33018943 (simplified stage-prediction/smart-alarm feasibility). | Feasibility/classification is not an outcome trial, Garmin validation, or proof of a “best minute.” | Do not market a perfect-cycle claim; require prospective outcome validation. |

## Contradictions and corrections applied

1. “Sleep score,” Body Battery, HRV and a single stage cannot be deterministic wake rules: retained and strengthened.
2. Population minimums and habitual duration are not an individual safe-shortening target: clarified.
3. Sleep-stage and “90-minute cycle” claims are too uncertain for primary decision authority: stage demoted to an optional, confidence-gated tie-breaker; 90-minute arithmetic is prohibited.
4. Existing Garmin/Apple links were treated as verified technical facts without an auditable contract/version/date: architecture documents now mark this as an unresolved feasibility gate.

## Unresolved evidence questions

1. What prediction target is clinically/product-usefully actionable: wake difficulty, next-day PVT, sleepiness, training outcome, or a composite?
2. What minimum history and outcome density permits individualized inference without overfitting?
3. Can an algorithm predict a user-specific acceptable wake window better than conservative fixed alarms out of sample?
4. Does any target Garmin model expose enough low-latency, reliable data for a night-time decision?
5. Can iPhone alarm delivery be guaranteed under the supported iOS/permission/focus/app-lifecycle states?
6. What decision loss correctly weights early waking, late waking, failed alarm delivery, regularity and accumulated restriction?

## Release gate

No autonomous earlier-than-conservative waking until primary-source bibliography, exact Garmin/iOS feasibility tests, pre-registered validation protocol and fallback-alarm reliability tests are complete.