---
kind: primary
routes:
  web: Web
steps:
- text: The Admin picks a language in My interface language and saves
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Interface language
  contexts:
    web:
      place: web::settings::view-settings
- text: The Product keeps it on the Admin's user account
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Interface language
  contexts:
    web:
      place: web::settings::view-settings
---

# Choose my language in View settings

## Trigger

An Admin sets their own language while adjusting the view.

## Outcome

The Admin's own interface language changes; other people keep theirs.
