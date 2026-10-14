---
kind: validation
routes:
  web: Web
steps:
- text: The Admin saves a user account with a taken or invalid login name, or a password under 8 characters and no OTP login
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - One-time code sign-in
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product refuses it and says why
  kind: product
  actor: admin
  entities: []
  contexts:
    web:
      place: web::settings::users-settings
---

# User account refused

## Trigger

An Admin mistypes a new account.

## Outcome

No account is created.
