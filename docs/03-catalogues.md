# Phase 03 — Catalogue providers and unified search

## Goal

Create one Favour catalogue interface over multiple real-world data providers.

## Domain model

Create a provider-neutral CatalogItem representation including:

- provider
- providerId
- category
- subtype
- title
- subtitle
- description where available
- releaseYear where relevant
- imageUrl
- canonicalUrl
- metadata

## Provider adapters

Film and TV:
TMDB

Books:
Google Books

Music:
MusicBrainz plus Cover Art Archive where appropriate

Places:
Create the interface/configuration placeholder for Google Places; implement full place discovery in Phase 08.

Use a replaceable adapter/service interface with operations similar to:

- search(query, options)
- getById(providerId)
- normalize(result)

All secret-bearing provider requests must run server-side.

## Unified search

Implement a server action or API layer for a call equivalent to:

searchCatalog({
  query,
  categories,
  limit
})

Return normalized items from enabled providers.

## SearchPicker

Build a reusable search picker with:

- debounced input
- image
- title
- useful subtitle
- category label
- loading state
- no-results state
- failure state
- keyboard navigation
- multi-category support

## Caching and limits

Use sensible server-side caching where provider terms allow it.

Avoid repeated identical calls.

Treat MusicBrainz conservatively. Implement a small server-side limiter/cache that respects its public-service expectations.

Set an identifying Favour MusicBrainz User-Agent.

## Development fallbacks

If a credential is missing:

- do not crash
- show a developer-facing warning
- allow fixture-backed results in development
- never silently present fixtures as real in production

## Tests

Add fixture-based adapter normalization tests.

Create /dev/catalog-search only in development for manual provider testing.

## Acceptance criteria

- unified search API/service exists
- adapters are isolated
- SearchPicker works with fixtures and any configured providers
- missing credentials degrade gracefully
- provider results normalize predictably
- tests/lint/typecheck/build pass

Update status and continue.
