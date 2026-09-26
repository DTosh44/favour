# Phase 09 — Ask Favour

## Goal

Create a natural-language entry point into Favour without turning the product into a generic chatbot.

## Route

/ask

Also add a tasteful Home entry field:

Ask Favour…

Suggested prompts:

- What should I watch tonight?
- Recommend a book for my holiday
- Where should I go for a weekend away?
- Surprise me
- Find something different

## Intent classification

Use structured output to classify into actions such as:

- recommend
- search
- compare
- surprise
- explain_taste

Possible fields:

- category
- location
- occasion
- mood
- constraints
- budget
- time available
- novelty
- count

Validate the structure.

## Service routing

Route the request through existing recommendation, catalogue and place services.

Do not let the model simply emit an unverified list of named products or venues.

## Result UX

Prefer rich recommendation cards over long chat prose.

Use short contextual text only when useful.

Example style:
You’ve got two hours tonight and tend to prefer thoughtful dramas, so I’d start here.

Then show verified recommendations.

## Conversation behaviour

Maintain lightweight context within a session.

Provide:

- New search
- Refine
- More like this

Do not optimise for endless conversation.

Store request history per user with a clear option to delete/clear it.

## Security and cost

- server-only model calls
- user-level rate limiting
- usage logging
- input validation
- safe error messages

## Acceptance criteria

- prompt classification works
- correct services are routed
- results are verified
- history can be cleared
- rate limiting exists
- relevant automated tests pass

Continue to Phase 10.
