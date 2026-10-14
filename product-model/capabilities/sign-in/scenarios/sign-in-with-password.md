---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user enters their login name and password and chooses Login
  kind: actor
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::sign-in::login
- text: The login name matches a user account that signs in with a password, and the password is right
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - One-time code sign-in
    - Password
  contexts:
    web:
      place: web::sign-in::login
- text: The Product starts a session and opens the fleet in the person's theme and language
  kind: product
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Role
    - Theme
    - Interface language
  contexts:
    web:
      place: web::sign-in::login
---

# Sign in with a password

## Trigger

A person opens SnapCon while User Access Management is on.

## Outcome

The person is signed in with their role; the session lasts while they keep using SnapCon and ends after 18 hours without use.

## Edge cases

- Login names are matched ignoring case.
