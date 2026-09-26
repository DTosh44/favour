# Phase 01 — Foundation and design system

## Goal

Create a polished, responsive Favour web application foundation and establish the selected Modern brand direction.

## Build

If the repository has no application yet, scaffold a current stable Next.js App Router project with TypeScript and Tailwind CSS.

Create a maintainable structure for:

- routes
- UI primitives
- domain components
- server services
- provider adapters
- validation
- database utilities
- types
- tests

## Brand

Display name: favour.

Tagline: find your next favourite.

Suggested tokens:

- Ink #0D1B1A
- Sage #4E7F73
- Mist #C8D9D1
- Sand #F6F5EF
- Cloud #EAEDE8

Define semantic CSS variables. Do not scatter hex values across components.

Use Plus Jakarta Sans where practical.

Create a reusable FavourLogo component. The word favour is ink; the full stop is sage.

## UI primitives

Create production-quality reusable primitives as needed:

- Button variants
- Card
- Pill/tag
- Avatar
- Page container
- Section heading
- Skeleton
- Empty state
- Error state
- Drawer/modal primitives where useful later

Keep primitives simple and accessible.

## Landing page

Hero:

favour.
find your next favourite.

Headline:
Find more of what you love.

Supporting copy:
Tell Favour what you already love and we’ll help you discover what you’ll love next.

Primary CTA:
Find my favourites

Secondary CTA:
How it works

Show four launch categories:

- Film & TV
- Books
- Music
- Travel

Three-step section:

1. Tell us what you love
2. We learn your taste
3. Discover your next favourite

Do not invent testimonials, user counts, partner logos or ratings.

Create tasteful visual placeholders if real imagery is unavailable.

## App shell

Create an authenticated-app shell placeholder ready for later phases.

Plan for:

Mobile nav:
- Home
- Search
- Saved
- Profile

Desktop:
Use an intentional desktop navigation/sidebar or header rather than stretching the phone layout.

## Accessibility

- semantic landmarks
- correct heading order
- keyboard access
- visible focus styles
- reduced-motion support
- sufficient colour contrast
- touch targets suitable for mobile

## Responsive testing

Check at approximately:

- 390px
- 768px
- 1280px
- 1440px

## Acceptance criteria

- app starts locally
- landing page looks recognisably like Favour
- design tokens exist
- reusable primitives exist
- responsive layouts are intentional
- no credential is required for this phase
- lint, typecheck, tests and production build pass

Update FAVOUR_BUILD_STATUS.md and continue to Phase 02.
