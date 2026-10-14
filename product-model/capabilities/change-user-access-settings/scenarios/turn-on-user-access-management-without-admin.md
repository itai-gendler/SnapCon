---
kind: validation
routes:
  web: Web
steps:
- text: The Admin turns on Enable user access management and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
- text: No user account has the Admin role
  kind: condition
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Role
  - entity: admin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product refuses and asks for an Admin account first
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::users-settings
---

# Require sign-in without an Admin account

## Trigger

An Admin turns sign-in on before creating any account.

## Outcome

Sign-in stays off, so nobody is locked out.
