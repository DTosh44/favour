# Phase 05 — Taste intelligence

## Goal

Implement the structured intelligence that turns explicit favourites and feedback into a useful taste profile.

## OpenAI integration

Use the current OpenAI Responses API or the current recommended equivalent at implementation time.

Use schema-constrained structured output.

Do not parse arbitrary free-form prose if a structured schema can express the same information.

All model calls are server-side.

## Inputs

Use permitted first-party/user data:

- explicit favourites
- likes/dislikes
- already-known signals
- selected categories
- user-entered preferences
- safe normalized metadata where appropriate

Do not ingest Spotify content.

## Structured taste schema

Implement a Zod/schema-backed output similar to:

overallSummary

descriptors:
- label
- confidence

noveltyPreference:
- familiar, balanced or adventurous
- confidence

mainstreamPreference:
- mainstream, mixed or independent
- confidence

categoryProfiles:
- film_tv: themes, genres, styles, pacing, signals
- books: themes, genres, styles, pacing, signals
- music: genres, moods, styles, signals
- travel: destination traits, pace, interests, signals

crossCategorySignals:
- trait
- evidence
- confidence

avoidSignals

searchSeeds per category

Improve the schema where useful, but preserve the distinction between explicit evidence and inference.

## Confidence

Do not present low-confidence inferences as facts.

Store confidence on inferred descriptors/signals.

Give the user a way later to reject an incorrect descriptor.

## Versioning

Every generated profile creates a new version.

Only one profile is active.

Provide services similar to:

- generateTasteProfile(userId)
- refreshTasteProfile(userId)
- getActiveTasteProfile(userId)

Do not regenerate on every tap.

Mark the profile dirty after meaningful feedback and refresh after a configurable threshold.

## Embeddings

Create a supporting embedding for the user’s taste using the current OpenAI embeddings API.

Use pgvector if it fits the Supabase setup cleanly.

Structured preferences remain canonical.

## Cost and resilience

- configurable model names
- minimal required context
- user-level rate limiting
- AI usage logging
- graceful failure
- do not discard a valid previous profile if a refresh fails

## /taste UI

Heading:
Your taste

Subheading:
The more you tell Favour what you love, the better it gets.

Display:

- overall summary
- descriptor pills
- category sections
- add more action
- explanation of how Favour learns
- Not me action on inferred descriptors

Copy:
Your taste is personal to your account and can be reset.

Do not show raw embeddings.

## Acceptance criteria

- structured profile generation exists
- schema validation exists
- profile versioning works
- failures are graceful
- /taste is real, not hard-coded user data
- model usage is logged
- tests cover validation/versioning/error handling
- quality checks pass

Continue to Phase 06.
