---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns on Enable user access management with no account yet and enters a login name and password for the first Admin
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - First name
    - Last name
    - Login name
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product creates the User account with the Admin role and password sign-in
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: creates
    facts:
    - First name
    - Last name
    - Login name
    - Email
    - Phone
    - Role
    - One-time code sign-in
    - Password
    - Groups
  contexts:
    web:
      place: web::settings::users-settings
---

# Create the first Admin

## Trigger

An Admin turns on sign-in for the first time.

## Outcome

An Admin account exists, so sign-in can be required.
