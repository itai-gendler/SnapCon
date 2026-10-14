---
kind: primary
routes:
  web: Web
steps:
- text: The Admin changes a user account's details or role and saves its row
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - First name
    - Last name
    - Login name
    - Email
    - Phone
    - Role
    - One-time code sign-in
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product saves them and records the change
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    facts:
    - First name
    - Last name
    - Login name
    - Email
    - Phone
    - Role
    - One-time code sign-in
    - Password
  contexts:
    web:
      place: web::settings::users-settings
---

# Edit a user account

## Trigger

A person's job changes.

## Outcome

The account has its new role from its next request.

## Edge cases

- A password left blank is kept.
- An account switched to OTP login can no longer sign in with its password.
