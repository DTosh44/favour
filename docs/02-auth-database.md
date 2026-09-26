# Phase 02 — Supabase, authentication and data model

## Goal

Add secure user accounts and the persistent data model that supports Favour’s recommendation loop.

## Authentication

Use current recommended Supabase SSR patterns for Next.js.

Support:

- email/password sign-up
- email/password sign-in
- sign-out
- password reset
- protected application routes

Keep architecture ready for Apple and Google auth later, but do not add them yet.

Routes:

- /sign-up
- /sign-in
- /forgot-password

Routing behaviour:

- new authenticated users go to /onboarding
- onboarded users go to /home

Use Favour styling throughout.

## Data model

Create migrations for these conceptual tables. Improve implementation details where needed while preserving behaviour.

profiles:
- id linked to auth.users
- display_name
- avatar_url optional
- onboarding_complete
- created_at
- updated_at

user_category_preferences:
- id
- user_id
- category
- enabled
- preference_strength optional
- created_at

catalog_items:
- id
- category
- subtype
- provider
- provider_id
- title
- subtitle
- description
- image_url
- canonical_url
- release_year optional
- metadata jsonb
- created_at
- updated_at

Require a sensible provider/provider_id/category uniqueness rule.

user_item_preferences:
- id
- user_id
- catalog_item_id
- preference: love, like, dislike, already_know
- source: onboarding, recommendation, manual or future sources
- created_at
- updated_at

saved_items:
- id
- user_id
- catalog_item_id
- created_at

taste_profiles:
- id
- user_id
- version
- summary
- attributes jsonb
- category_profiles jsonb
- embedding/vector where supported cleanly
- generated_at
- active

recommendation_batches:
- id
- user_id
- category optional
- context jsonb
- created_at

recommendations:
- id
- user_id
- catalog_item_id
- category
- score
- reason
- status
- recommendation_batch_id
- generated_at

feedback_events:
- id
- user_id
- catalog_item_id
- recommendation_id optional
- event_type
- metadata jsonb
- created_at

ai_usage:
- id
- user_id optional
- operation
- model
- input_tokens optional
- output_tokens optional
- estimated_cost optional
- success
- created_at

## Security

Apply Row Level Security to every user-owned table.

Users must never read or mutate another user’s:

- profile
- category preferences
- item preferences
- saves
- taste profiles
- recommendation batches
- recommendations
- feedback
- AI usage

catalog_items may be globally readable but not arbitrarily writable by clients.

Keep administrative credentials server-only.

## Developer experience

- create Supabase client helpers for browser and server use
- generate or maintain database TypeScript types
- create .env.example
- create setup documentation
- gracefully detect missing Supabase configuration in development rather than failing opaquely

## Acceptance criteria

- auth flows are implemented
- private routes are protected
- migrations are present
- RLS policies are present
- no secret is bundled client-side
- /home exists as an authenticated placeholder
- lint/typecheck/tests/build pass

If Supabase is not configured, mark live verification clearly but continue to Phase 03.
