# Phase 07 — Main product experience

## Goal

Build the main Favour interface around the working recommendation engine.

## Routes

- /home
- /for-you
- /category/[category]
- /item/[id]
- /search
- /saved
- /taste
- /profile

## Navigation

Mobile:
- Home
- Search
- Saved
- Profile

Desktop:
Create an intentional wider-screen structure.

## Home

Show the Favour wordmark.

Use a time-appropriate greeting with the user’s first name.

Copy:
Here are some new favourites for you.

Include a strong hero recommendation and finite sections such as:

- For you
- Film & TV
- Books
- Music
- Places worth knowing

Avoid infinite scroll.

Use compact horizontal rails on mobile where useful.

## Recommendation cards

Include:

- authentic image
- category label
- title
- subtitle
- concise reason or Because you loved…
- save action
- detail action

## Detail page

Show:

- imagery
- title
- category
- useful metadata
- description
- personalised reason
- canonical/provider action where useful

Feedback actions must work:

- Love it
- Like it
- Not for me
- Already know it
- Save to Favourites

Persist immediately.

Use optimistic UI only when rollback is safe.

Not for me should offer a replacement recommendation.

## Search

Global search uses the unified catalogue.

Known items can be marked Love, Like or Save.

Those actions teach Favour.

## Saved

Filters:

- All
- Film & TV
- Books
- Music
- Travel

Allow unsave.

## Empty states

No recommendations:
Tell Favour a little more about what you love.

No saves:
Things worth coming back to will appear here.

## Acceptance criteria

- all routes are functional
- feedback persists
- save/unsave persists
- replacement recommendation works
- search can teach Favour
- layouts feel designed on phone and desktop
- no infinite feed
- quality checks pass

Continue to Phase 08.
