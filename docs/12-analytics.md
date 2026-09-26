# Phase 12 — Product analytics and admin

## Goal

Measure whether Favour is useful without building invasive surveillance.

## Questions to answer

- How many users complete onboarding?
- How many favourites are added?
- Which categories are used?
- Are recommendations opened?
- How often are Love, Like, Not for me and Already know it used?
- How many recommendations are saved?
- How often is Ask Favour used?
- Do users return?
- How many AI calls are made?
- What is approximate AI cost per active user?
- What provider/API failure rates occur?

## Event design

Prefer first-party structured events stored safely in the application database or a privacy-conscious analytics tool.

Do not introduce session replay, fingerprinting or unnecessary third-party tracking.

## Admin

Create a small internal admin route protected through a server-side allowlist or stronger admin-role mechanism.

Show aggregated metrics:

- users
- onboarding completion
- category use
- recommendation interactions
- feedback breakdown
- saves
- Ask Favour usage
- AI usage and estimated cost
- provider health/errors

Do not expose individual taste profiles in normal analytics views.

## Logging

Add useful structured server logs for provider/model failures without leaking credentials or unnecessarily logging private prompt content.

## Acceptance criteria

- key product metrics are measurable
- admin access is protected
- no invasive tracking
- AI/provider costs and failures are visible
- tests cover admin access control

Continue to Phase 13.
