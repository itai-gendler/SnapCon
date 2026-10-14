---
kind: validation
routes:
  web: Web
steps:
- text: The Admin changes the role of the only Admin account and saves
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Role
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product refuses so that an Admin always remains
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::users-settings
---

# Demoting the last Admin refused

## Trigger

An Admin tries to give up the last Admin role.

## Outcome

The account keeps the Admin role.
