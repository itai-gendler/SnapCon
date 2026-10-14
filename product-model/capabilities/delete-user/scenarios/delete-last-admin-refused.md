---
kind: validation
routes:
  web: Web
steps:
- text: The Admin removes the only Admin account, or the only account while the tunnel is on
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - Role
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product refuses and says why
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

# Deleting the last Admin refused

## Trigger

An Admin tries to remove the last way in.

## Outcome

The account stays.
