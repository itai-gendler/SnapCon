---
kind: validation
routes:
  web: Web
steps:
- text: The Admin deletes a Printer pool that still has members, or the Unassigned pool
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
- text: The Product refuses and says to reassign its members first
  kind: product
  actor: admin
  entities:
  - entity: printer-pool
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::queue-management-settings
---

# Deleting a pool in use refused

## Trigger

An Admin deletes a pool in use.

## Outcome

The pool stays.
