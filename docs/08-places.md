# Phase 08 — Travel and Places

## Goal

Add real-world place discovery while keeping AI responsible for intent and the provider responsible for entity truth.

## Provider

Use Google Places API (New) server-side.

Never expose GOOGLE_PLACES_API_KEY to the browser.

Use field masks and request only fields the UI actually needs.

## Two levels of travel

Destination-level recommendations:

- cities
- regions
- islands
- broad destinations

Specific place recommendations:

- hotel
- restaurant
- museum
- bar
- attraction
- activity

## Structured place intent

Convert user request plus taste profile into a validated structure similar to:

- placeType
- location
- characteristics
- budget or price preference where supported
- date/occasion context where relevant
- accessibility constraints if explicitly provided
- novelty preference

Example:
Find me a hotel in Copenhagen I’d like.

Favour should infer search characteristics from the user’s taste, then search the real provider.

## Entity truth

Specific venues shown to the user must originate from or be resolved by the place provider.

Do not let a model invent a venue and present it as real.

Persist place provider IDs.

Respect provider attribution/photo requirements.

## UI

Create Favour-styled place cards and detail presentation.

Use imagery strongly.

Explain why a place fits the user’s taste using grounded signals.

## Failure modes

Handle clearly:

- missing key
- billing disabled
- quota/rate limit
- zero results
- provider timeout
- missing photo

Do not silently substitute fake production data.

## Cost control

Use narrow field masks.

Cache where provider terms permit.

Do not request expensive fields before the user needs them.

## Acceptance criteria

- structured place intent exists
- server provider adapter exists
- real results normalize to CatalogItem or an appropriate domain model
- key is not client-exposed
- graceful errors exist
- tests cover intent/normalization
- quality checks pass

Continue to Phase 09.
