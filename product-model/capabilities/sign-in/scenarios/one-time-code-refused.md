---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user enters a code that is wrong, expired, or past its fifth attempt
  kind: actor
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::sign-in::login
- text: The code does not match, is older than ten minutes, or has had five attempts
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
  contexts:
    web:
      place: web::sign-in::login
- text: The Product refuses the code and, when it expired or ran out of attempts, asks for a new one
  kind: product
  actor: regular-user
  entities: []
  contexts:
    web:
      place: web::sign-in::login
---

# One-time code refused

## Trigger

A person enters a one-time code that no longer works.

## Outcome

Nobody is signed in; an expired or exhausted code is discarded and a new one must be requested.
