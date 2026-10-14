---
kind: primary
routes:
  web: Web
steps:
- text: The Admin picks a Printer pool under Queue on a printer
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Printer pool
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Printer queue is idle and empty
  kind: condition
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product assigns the printer to the Printer pool and records the change
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: changes
    facts:
    - Printer pool
  - entity: printer-pool
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::printer-settings
---

# Move a printer to a pool

## Trigger

A printer joins a group of identical printers.

## Outcome

The printer can receive jobs sent to the pool.
