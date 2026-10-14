---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user enters a login name and a wrong password and chooses Login
  kind: actor
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::sign-in::login
- text: The login name is unknown or the password does not match
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - Password
  contexts:
    web:
      place: web::sign-in::login
- text: The Product refuses with the same message for both cases and records the failed sign-in
  kind: product
  actor: regular-user
  entities: []
  contexts:
    web:
      place: web::sign-in::login
---

# Sign-in refused

## Trigger

A person signs in with a mistyped login name or password.

## Outcome

Nobody is signed in; the message does not reveal whether the login name exists.

## Edge cases

- An account that signs in with one-time codes is told to request a code instead of using a password.
