# Phase 04 — Onboarding

## Goal

Create the first key Favour experience: quickly teach the app enough about a new user to begin recommending.

## Product line

Headline:
Start with five favourites.

Copy:
Pick a few things you already love. The more you tell Favour, the better your recommendations become.

## Flow

### Step 1 — Welcome

Briefly explain that Favour learns what a person likes across different parts of life.

CTA:
Build my taste

### Step 2 — Choose interests

Selectable cards:

- Film & TV
- Books
- Music
- Travel & Places

Allow multiple selection.

Recommend at least three categories, but do not require every category.

### Step 3 — Add favourites

Use the real unified catalogue search.

Require at least five total favourites.

Allow more than five.

Encourage variety:
Try adding favourites from more than one category.

Show selected items with:

- image
- title
- subtitle
- category

Allow removal/undo.

Store selected catalogue items and create user_item_preferences with preference love and source onboarding.

### Travel onboarding

If Places is not live yet, support a clearly identified free-text destination favourite.

Store it in a structured temporary form so it can later be reconciled with a provider result.

### Step 4 — Taste generation

Create a tasteful transition state with rotating copy such as:

- Finding the patterns…
- Joining the dots…
- Building your taste…

Do not use fake progress percentages.

Wire this to the taste service contract. If Phase 05 is not yet available, keep a temporary integration boundary rather than faking AI.

### Step 5 — Complete

Once taste generation exists, send the user to /taste.

Mark onboarding_complete only when enough onboarding data is safely persisted.

## Reliability

Persist onboarding progress so a refresh does not destroy selections.

Mobile-first.

Avoid turning onboarding into a long personality quiz.

## Acceptance criteria

- authenticated new user can complete onboarding
- at least five favourites are enforced
- selections persist
- real catalogue items are stored correctly
- travel fallback is explicit and structured
- refresh does not lose progress
- tests/lint/typecheck/build pass

Update status and continue.
