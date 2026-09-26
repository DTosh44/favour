# Phase 14 — Deployable beta

## Goal

Prepare Favour for a small external beta and leave an explicit operational handoff.

## Hosting

Assume Vercel unless the repository is already intentionally configured elsewhere.

Prepare:

- production environment variable documentation
- deployment configuration
- Supabase production setup notes
- migrations
- authentication redirect/callback configuration
- secure production defaults
- error boundaries
- 404/error pages
- public/private robots behaviour
- metadata
- Open Graph metadata
- favicon and PWA/app icon based on the Favour mark
- manifest where appropriate

Public marketing pages may be indexable.

Private account routes must not be indexed.

## Resilience

Confirm external API failures degrade gracefully.

Add lightweight health checks where useful.

Ensure fixture/mock modes cannot accidentally appear as genuine production recommendations.

## Beta test plan

Create BETA_TEST_PLAN.md for an initial approximately 10-user beta.

Include:

- participant profile
- onboarding tasks
- recommendation tasks
- Ask Favour tasks
- travel task
- feedback questions
- metrics to observe
- bugs to watch
- success criteria for moving beyond beta

Key qualitative question:
Does Favour understand my taste surprisingly quickly?

## Final verification

Run the complete quality suite.

Fix failures.

Review FINAL_MVP_CHECKLIST.md and update it.

## Final handoff

Update FAVOUR_BUILD_STATUS.md with:

1. deployable-product readiness
2. exact manual setup remaining
3. missing environment variables
4. external accounts/API keys required
5. known limitations
6. live integrations still requiring verification
7. top recommended post-MVP features

Do not call the beta ready if the critical onboarding → taste → recommendation → feedback loop is not functioning.

When this phase is complete, stop and present the handoff rather than expanding scope automatically.
