---
kind: primary
routes:
  web: Web
steps:
- text: The Admin renames a Printer pool
  kind: actor
  actor: admin
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::queue-management-settings
- text: The Product saves the new name and records it
  kind: product
  actor: admin
  entities:
  - entity: printer-pool
    effect: changes
    facts:
    - Name
  contexts:
    web:
      place: web::settings::queue-management-settings
---

# Rename a pool

## Trigger

A pool's purpose changes.

## Outcome

The Print Farm view shows the new name.
