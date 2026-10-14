---
kind: primary
routes:
  web: Web
steps:
- text: The Admin deletes an empty Printer pool and confirms
  kind: actor
  actor: admin
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Name
    - Built-in
  contexts:
    web:
      place: web::settings::queue-management-settings
- text: The Product deletes it and records it
  kind: product
  actor: admin
  entities:
  - entity: printer-pool
    effect: removes
  contexts:
    web:
      place: web::settings::queue-management-settings
---

# Delete a pool

## Trigger

A pool is no longer used.

## Outcome

The pool is gone.
