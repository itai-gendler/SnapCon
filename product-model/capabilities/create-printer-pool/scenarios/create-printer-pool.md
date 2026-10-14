---
kind: primary
routes:
  web: Web
steps:
- text: The Admin types a pool name and chooses Add Pool
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
- text: The Product creates the Printer pool with manual bed clear and auto-balance off, and records it
  kind: product
  actor: admin
  entities:
  - entity: printer-pool
    effect: creates
    facts:
    - Name
    - Bed clear
    - Auto-balance
    - Built-in
  contexts:
    web:
      place: web::settings::queue-management-settings
---

# Create a pool

## Trigger

A set of identical printers should share work.

## Outcome

Printers can be assigned to the pool.
