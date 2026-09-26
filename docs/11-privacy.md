# Phase 11 — Privacy, settings and security

## Goal

Give users control over their account and taste data, and complete the baseline security review before beta.

## Profile/settings

/profile should support:

- change display name
- change password
- manage enabled categories
- notification preference placeholder if notifications are not yet live
- sign out

## Data controls

Add:

- Download my data
- Reset my taste
- Delete my account

Reset my taste:

- require confirmation
- remove/reset taste profiles, preferences, recommendations and related personal learning data
- preserve the account

Delete account:

- require explicit confirmation
- securely remove or appropriately anonymise user-owned data
- remove authentication identity through a safe server-side flow

## Privacy and terms

Create:

- /privacy
- /terms

Use honest draft wording suitable for later professional/legal review.

Do not make unsupported claims.

## Analytics consent

Avoid unnecessary tracking.

If analytics requiring consent is introduced, implement appropriate controls.

## Security audit

Review and fix:

- client/server boundaries
- API key exposure
- authentication protection
- RLS
- request validation
- endpoint rate limits
- error leakage
- unsafe HTML/content
- XSS risks from provider text
- unsafe redirects
- safe external URLs
- account deletion permissions
- development-only routes disabled in production

Treat all external descriptions and URLs as untrusted input.

## Acceptance criteria

- reset works
- deletion flow is safely implemented
- download/export works in a useful format
- privacy/terms pages exist
- security issues found are fixed or documented
- tests cover destructive actions and access control
- quality checks pass

Continue to Phase 12.
