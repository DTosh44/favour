# Favour — Codex Agent Brief

## Mission

Build **Favour**, a polished consumer recommendation app that learns what a person already loves and helps them discover what they will love next.

**Brand:** `favour.`  
**Tagline:** `find your next favourite.`

This file is the permanent product and engineering brief. Read it before every phase, then read `FAVOUR_BUILD_PLAN.md`, `FAVOUR_BUILD_STATUS.md`, and the current phase document in `docs/`.

## Core proposition

Favour is a personal taste engine, not a generic content feed.

A user tells Favour what they already love. Favour learns explicit and inferred taste signals, then recommends real, verified things across multiple categories.

MVP categories:

1. Film & TV
2. Books
3. Music
4. Travel & Places

Future categories, outside the MVP unless explicitly added later:

- Fashion and style
- Restaurants and food
- Home and interiors
- Art
- Podcasts
- Games
- Experiences
- Gifts
- Products

## Core user journey

1. Land on Favour.
2. Create an account.
3. Select categories of interest.
4. Add at least five existing favourites.
5. Generate a structured personal taste profile.
6. See personalised recommendations.
7. React using:
   - Love it
   - Like it
   - Not for me
   - Already know it
   - Save
8. Use those signals to improve future recommendations.
9. Browse by category.
10. View and refine **Your taste**.
11. View Saved items.
12. Use **Ask Favour** for natural-language requests such as:
   - What should I watch tonight?
   - Recommend a book for my holiday.
   - Where should I go for a weekend away?
   - Surprise me.
   - Find me something different that I might love.

## Product principles

- Favour should feel **curated**, finite and useful rather than infinite and addictive.
- The key product moment is: **“Favour understands my taste surprisingly quickly.”**
- Recommendations must feel personal and explainable.
- Cross-category taste understanding is a differentiator.
- Do not infer or expose sensitive personal traits.
- Do not invent real-world entities.
- AI interprets and ranks; external catalogues verify that items exist.
- Do not show fake match percentages.
- Avoid dark patterns, streaks, engagement gimmicks and endless scroll.

## Brand direction

Selected direction: **Modern**.

Personality:

- clean
- contemporary
- intelligent
- friendly
- understated
- premium without being exclusive
- editorial rather than “tech startup”
- calm and confident

Primary wordmark:

`favour.`

The word is dark ink. The full stop is sage and should act as a subtle brand device.

Suggested design tokens:

- Ink: `#0D1B1A`
- Sage: `#4E7F73`
- Mist: `#C8D9D1`
- Sand: `#F6F5EF`
- Cloud: `#EAEDE8`

Use semantic CSS variables rather than scattering hard-coded colours through components.

Typography:

- Prefer Plus Jakarta Sans or an equivalent production-safe modern sans-serif.
- Strong, clean typographic hierarchy.
- Generous whitespace.

UI direction:

- mobile-first
- beautiful at ~390px wide
- intentional desktop layouts
- restrained corner radii
- restrained borders
- minimal shadows
- strong use of authentic imagery
- subtle motion
- no glassmorphism
- no neon
- no loud gradients
- no generic AI sparkle/robot imagery
- no cluttered dashboards

## Technical direction

Use current stable, production-appropriate versions of:

- Next.js
- TypeScript
- App Router
- Tailwind CSS
- Supabase for Postgres + authentication
- OpenAI for structured taste intelligence, embeddings and recommendation reasoning
- Zod for schemas and validation

External data providers:

- TMDB: film and TV
- Google Books: books
- MusicBrainz + Cover Art Archive: music
- Google Places API (New): real-world places

Important: **do not use Spotify content as input to an AI model.**

Provider architecture must use replaceable adapters/interfaces so catalogue vendors can change later.

## AI rules

- Prefer structured outputs over parsing arbitrary model prose.
- Keep all AI/API secrets server-side.
- Keep model selection configurable.
- Log AI usage and failures.
- Rate-limit AI endpoints.
- Keep structured user preferences canonical; embeddings are a supporting signal, not the sole truth.
- Distinguish directly known facts from inferred taste signals.
- Store confidence on inferred signals.
- Do not surface low-confidence inferences as fact.
- Verify named recommendations against an external provider before displaying them.

## Security and privacy

- Never commit credentials.
- Maintain `.env.example`.
- Use Supabase Row Level Security.
- Users must not read or mutate other users’ private data.
- Validate all external input.
- Treat external provider content as untrusted.
- Sanitize/escape where appropriate.
- Protect private routes.
- Use safe URL handling.
- Rate-limit abuse-prone endpoints.
- Provide account deletion and taste reset before public beta.

## Engineering standards

- Strict TypeScript.
- Avoid `any` unless genuinely necessary and justified.
- Keep components and services reasonably small.
- Separate UI, domain logic, provider adapters and server-only code.
- Prefer reusable components.
- Add loading, empty and error states.
- Build accessibility in from the start.
- Buttons must work; do not leave important fake interactions.
- Development fixtures are allowed only when external credentials are absent.
- Production must never silently present mock data as real.
- Preserve working code; do not rewrite stable areas without a reason.

## Testing and phase completion

For every phase:

1. Read this file, the build plan, status file and current phase spec.
2. Inspect the existing implementation before changing it.
3. Implement the phase.
4. Add/update tests.
5. Run lint.
6. Run type checking.
7. Run tests.
8. Run a production build when the project is capable of it.
9. Fix legitimate failures.
10. Manually exercise the relevant user journey where possible.
11. Update `FAVOUR_BUILD_STATUS.md`.
12. Do not mark a phase complete unless its acceptance criteria are met.

## Working autonomously

The build plan is deliberately designed so Codex can proceed without repeated user prompts.

- Work through phases in numerical order.
- Continue automatically after completing a phase.
- Do not wait for confirmation between phases.
- If credentials are missing, implement the interface, environment variables, graceful error state and development fixture path, then continue with non-blocked work.
- Stop only when a genuinely external action is required and there is no meaningful unblocked work left.
- When blocked, document the exact required action in `FAVOUR_BUILD_STATUS.md`.
- Never invent a credential or claim an integration works when it has not been tested against a real provider.

## Source of truth order

When instructions conflict, use this precedence:

1. User’s latest explicit instruction
2. `AGENTS.md`
3. `FAVOUR_BUILD_PLAN.md`
4. Current `docs/NN-*.md`
5. Existing implementation conventions

Keep the product recognisably Favour throughout.
