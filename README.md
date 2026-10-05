# Smart Wake Intelligence

Evidence-driven adaptive alarm R&D knowledge base.

## Mission
Build an adaptive wake system that selects the earliest sufficiently safe and effective wake moment inside a user-defined window, while protecting long-term sleep need, recovery, regularity and health.

**Target: minimum safe effective sleep, not minimum sleep.**

## Non-negotiable principles
- Never use the 90-minute sleep-cycle rule.
- Never treat Garmin sleep stages as EEG/PSG.
- Never systematically force a fixed short sleep duration.
- Never let poor sleep metrics create an unbounded late wake-up.
- Never use HRV or one metric as the sole decision variable.
- Use personal baselines and longitudinal trends.
- Separate sleep sufficiency, recovery, physiological stability, circadian readiness and wake readiness.
- Represent uncertainty and confidence explicitly.
- Use conservative safety floors and a hard maximum wake time.
- Learn from next-day outcomes without allowing subjective adaptation to hide objective performance loss.
- Optimize over weeks, not isolated nights.

## Model
The wake decision combines sleep opportunity, recent sleep history/sleep pressure, regularity, physiological deviation from personal baseline, circadian timing, wake-readiness, and sleep-stage information as a secondary signal. Morning and daytime outcomes provide longitudinal feedback.

The conceptual foundation is the two-process model: homeostatic sleep pressure (Process S) plus circadian drive (Process C).

## Evidence policy
Every important claim is classified as established/high confidence, supported but limited, plausible hypothesis, or unknown/requires validation. Correlation must not be presented as causation. Primary literature is preferred.

## Product boundary
Garmin is primarily the physiological sensing source. The alarm sounds on the iPhone, which is placed away from the bed. Architecture must respect iOS background constraints and should not assume arbitrary continuous phone processing overnight.

## Repository map
- `PROMPTS/` — Hermes operating prompts.
- `RESEARCH/` — scientific evidence and source registry.
- `SCIENCE/` — evidence translated into model principles.
- `PRODUCT/` — product vision and requirements.
- `ARCHITECTURE/` — Garmin, iOS and data-flow constraints.
- `ROADMAP.md` — staged R&D and validation plan.

## Safety
This is a wellness/product system, not a medical diagnostic device. It must communicate uncertainty and must not claim that consumer wearable data can determine exact sleep need.

## Status
Phase 0 — scientific and technical R&D before production implementation.
