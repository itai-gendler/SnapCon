---
kind: primary
routes:
  web: Web
steps:
- text: The Admin removes a user account and confirms
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product deletes it, ends the session when it was the Admin's own, and records it
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: removes
  contexts:
    web:
      place: web::settings::users-settings
---

# Delete a user account

## Trigger

Someone leaves.

## Outcome

The account no longer signs in; its past activity stays in the log.
