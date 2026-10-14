---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user enters their login name and chooses Send me a code instead
  kind: actor
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::sign-in::login
- text: The user account signs in with one-time codes and one-time code delivery is configured
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - One-time code sign-in
    - Email
  - entity: settings
    effect: reads
    facts:
    - One-time code delivery
    - Email sender
  contexts:
    web:
      place: web::sign-in::login
- text: The Product sends an eight-character code that expires in ten minutes by email, ntfy.sh or Telegram
  kind: product
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - Email
  - entity: settings
    effect: reads
    facts:
    - One-time code delivery
  contexts:
    web:
      place: web::sign-in::login
- text: The Regular user enters the code and chooses Verify
  kind: actor
  actor: regular-user
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::sign-in::login
- text: The Product accepts the code once and starts a session
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

# Sign in with a one-time code

## Trigger

A person whose account uses one-time codes opens SnapCon.

## Outcome

The person is signed in; the code cannot be used again.

## Edge cases

- A request for a login name that does not exist, does not use codes, or has no email for email delivery gets the same generic refusal.
