---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns on Auto-balance on a Printer pool of the Print Farm view
  kind: actor
  actor: admin
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Name
    - Auto-balance
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product keeps it on the Printer pool
  kind: product
  actor: admin
  entities:
  - entity: printer-pool
    effect: changes
    facts:
    - Auto-balance
  contexts:
    web:
      place: web::fleet::print-farm
---

# Turn on auto-balance for a pool

## Trigger

Some printers of a pool sit idle while others have a backlog.

## Outcome

Work moves between the pool's printers by itself.
