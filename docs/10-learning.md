# Phase 10 — Feedback and learning

## Goal

Make user interaction change future recommendations in a meaningful, testable way.

## Signal strengths

Model different strengths rather than treating every event equally.

Suggested semantics:

- onboarding favourite: strong positive
- Love it: strong positive
- Like it: positive
- Save: weak/moderate positive intent
- Already know it: neutral taste signal but strong discovery exclusion
- Not for me: negative

Tune weights through configuration rather than hard-coded mystery numbers spread through the codebase.

## Category effects

Feedback should affect its own category strongly.

Cross-category impact should be weaker and only used when supported by repeated/high-confidence patterns.

Liking a film must not arbitrarily overhaul restaurant/travel taste.

## Cross-category signals

Support non-sensitive recurring themes such as:

- minimalist
- design-led
- nostalgic
- experimental
- independent
- luxurious
- outdoors-oriented
- traditional
- atmospheric
- playful
- calm

Do not infer sensitive characteristics, protected traits, health state, political beliefs or similarly inappropriate personal conclusions.

## Refresh policy

After enough meaningful new feedback:

- mark profile dirty
- refresh structured taste profile
- invalidate or de-prioritise stale recommendation batches where appropriate
- generate new candidates when requested

Do not call AI after every tap.

Use configurable thresholds.

## User feedback

A subtle message such as:
Your taste is getting sharper.

Avoid points, levels, streaks or gamified scores.

## Developer diagnostics

Create a development-only diagnostics page showing:

- current signal weights
- active profile version
- dirty state
- recent feedback
- recommendation scoring components

Never expose this publicly in production.

## Tests

Demonstrate that:

- Love increases relevant ranking
- Not for me reduces/excludes relevant ranking
- Already know it removes discovery repetition
- unrelated categories are not over-adjusted
- threshold-based refresh works

## Acceptance criteria

Learning is observable, bounded and covered by tests.

Continue to Phase 11.
