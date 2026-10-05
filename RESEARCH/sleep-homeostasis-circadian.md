# Sleep Homeostasis and Circadian Timing

Sleep/wake propensity is commonly described through interacting homeostatic and circadian processes.

Source:
https://pubmed.ncbi.nlm.nih.gov/26762182/

## Process S
Represents accumulated homeostatic sleep pressure. It is affected by prior wake and sleep.

## Process C
Represents circadian timing and biological drive that changes across the day/night.

## Product consequence
A wake decision should not infer readiness solely from "hours slept". Two nights with equal sleep duration can have different timing and recovery contexts.

## Design
Maintain separate estimates for:
- sleep pressure;
- circadian phase/readiness;
- observed sleep opportunity;
- uncertainty.

Do not claim precise circadian phase unless the available data justify it.
