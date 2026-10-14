---
kind: primary
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
- text: A user account with the Admin role exists
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
- text: The Product requires sign-in from then on and records the change
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
---

# Require sign-in

## Trigger

An Admin wants to control who uses SnapCon.

## Outcome

Everyone must sign in, and roles and groups apply.
