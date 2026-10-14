---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns off Auto-balance on a Printer pool
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
- text: The Product keeps it off
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

# Turn off auto-balance for a pool

## Trigger

Jobs must stay on the printers they were sent to.

## Outcome

Each queue keeps its own jobs.
