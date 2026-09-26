# Favour Build Plan

## Purpose

This file is the orchestration plan for building Favour from an empty repository into a working external beta.

Codex should work through the phases below in order, without waiting for a new user prompt between phases.

Always read:

1. AGENTS.md
2. this file
3. FAVOUR_BUILD_STATUS.md
4. the current phase file in docs/

## Autonomous execution contract

At the start of a session:

1. Inspect the repository.
2. Read FAVOUR_BUILD_STATUS.md.
3. Identify the first phase not marked COMPLETE.
4. If it is BLOCKED, determine whether other meaningful work in that phase can continue without the blocker.
5. Continue implementation.
6. Do not redo completed work unless a regression or architecture problem requires it.
7. Update the status file before ending a session.

After every phase:

- run lint
- run type checking
- run automated tests
- run a production build when the project supports it
- fix legitimate failures
- manually exercise the relevant flow where possible
- update FAVOUR_BUILD_STATUS.md
- record blockers honestly
- continue directly to the next phase

Do not pause for user approval between phases.

Missing credentials are not automatically a reason to stop. Build the provider adapter, environment configuration, fixtures, graceful error state and tests, then continue. Stop only when there is no meaningful unblocked work left.

## MVP definition

A new user can:

1. visit a polished Favour landing page
2. create an account
3. choose interests
4. add at least five real favourites
5. generate a structured taste profile
6. receive verified recommendations across multiple categories
7. react with Love, Like, Not for me, Already know it and Save
8. see that feedback influence future recommendations
9. search for known items and teach Favour more
10. view Saved items
11. inspect and refine Your taste
12. Ask Favour a natural-language recommendation question
13. receive real place recommendations where provider credentials are available
14. reset taste or delete the account

## Architecture

Preferred stack:

- current stable Next.js
- TypeScript
- App Router
- Tailwind CSS
- Supabase Postgres and Auth
- OpenAI server-side services
- Zod schemas
- Vitest or an equivalent lightweight test runner
- Playwright for critical end-to-end flows once the UI is stable

Provider adapters:

- TMDB for film and TV
- Google Books for books
- MusicBrainz and Cover Art Archive for music
- Google Places API (New) for places

Keep providers replaceable through domain interfaces.

## Quality gates

A phase is COMPLETE only if:

- the requested functionality exists
- primary interactions are not fake
- TypeScript passes
- lint passes
- tests relevant to the phase pass
- error/loading/empty states exist
- secrets are not exposed
- accessibility is considered
- status has been updated

Where an integration cannot be live-tested because a credential is missing, record it as NEEDS LIVE VERIFICATION rather than pretending it is complete.

## Phase order

1. Foundation and design system — docs/01-foundation.md
2. Supabase, authentication and data model — docs/02-auth-database.md
3. Catalogue providers and unified search — docs/03-catalogues.md
4. Onboarding — docs/04-onboarding.md
5. Taste intelligence — docs/05-taste-engine.md
6. Recommendation engine — docs/06-recommendations.md
7. Main product experience — docs/07-main-app.md
8. Travel and Places — docs/08-places.md
9. Ask Favour — docs/09-ask-favour.md
10. Feedback and learning — docs/10-learning.md
11. Privacy, settings and security — docs/11-privacy.md
12. Product analytics and admin — docs/12-analytics.md
13. Full QA and production polish — docs/13-qa.md
14. Deployable beta — docs/14-beta.md

## Expected external configuration

Keep .env.example current. Anticipated production values include:

- NEXT_PUBLIC_SUPABASE_URL
- NEXT_PUBLIC_SUPABASE_ANON_KEY or the current Supabase publishable-key equivalent
- SUPABASE_SERVICE_ROLE_KEY only where a server-only administrative operation truly requires it
- OPENAI_API_KEY
- OPENAI_TASTE_MODEL
- OPENAI_EMBEDDING_MODEL
- TMDB_ACCESS_TOKEN
- GOOGLE_BOOKS_API_KEY where appropriate
- GOOGLE_PLACES_API_KEY
- MUSICBRAINZ_USER_AGENT
- ADMIN_USER_IDS or a safer equivalent

Never commit real values.

## Scope discipline

Do not expand the MVP into fashion, restaurants, homeware, podcasts, games or ecommerce before the core recommendation loop works.

Do not add social feeds, streaks, points, leaderboards or engagement mechanics.

The product should remain calm, useful and personal.
