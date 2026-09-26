# Phase 06 — Recommendation engine

## Goal

Turn a taste profile into real, verified, personalised recommendations.

## Inputs

Use:

- active taste profile
- explicit loves
- likes
- dislikes
- already-known items
- saved items
- previously shown recommendations
- requested category
- optional user request context

Never recommend something explicitly disliked.

Strongly avoid already-known items in discovery results.

## Pipeline

Implement a staged pipeline:

1. Load active taste profile.
2. Create structured candidate intents/search seeds.
3. Generate candidate entities or provider searches.
4. Resolve and verify candidates through the correct provider.
5. Reject anything that cannot be confidently verified.
6. Deduplicate.
7. Score.
8. Generate a concise grounded reason.
9. Store batch and recommendations.
10. Return a finite curated list.

## Category strategy

Film/TV:
Use TMDB search/discover/similar/recommendation capabilities where useful.

Books:
Generate search seeds and resolve through Google Books.

Music:
AI may propose artist/album candidates from user-provided taste, but every displayed entity must resolve through MusicBrainz.

Do not send Spotify API content to an AI model.

Travel:
Support destination-level recommendations in this phase. Specific hotels/restaurants/venues come in Phase 08.

## Scoring

Use an internally explainable score composed from factors such as:

- taste match
- novelty
- category relevance
- confidence
- feedback adjustment
- repetition penalty
- diversity adjustment

Do not show users invented percent-match numbers.

## Reasons

Generate concise personalised reasoning grounded in known taste signals and verified metadata.

Example style:
Because you tend to favour thoughtful science fiction, slower storytelling and visually distinctive films.

Avoid fabricated facts.

## Diversity

A list should not contain ten near-identical items.

Balance style, era, familiarity and mainstream/independent tendencies where appropriate.

Allow one Wildcard when confidence and novelty settings support it.

## Resilience

If AI fails, keep existing valid cached recommendations and allow retry.

If one provider fails, preserve valid results from providers that succeeded.

## Required tests

- disliked item exclusion
- already-known handling
- duplicate removal
- unverified AI candidate rejection
- empty taste profile
- partial provider failure
- reason schema validation

## Acceptance criteria

The recommendation service can generate, verify, score, store and return a personalised batch without allowing hallucinated entities into the UI.

Continue to Phase 07.
