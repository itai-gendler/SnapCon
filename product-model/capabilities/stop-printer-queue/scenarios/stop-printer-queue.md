---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Stop Queue on a printer and confirms
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product marks the Printer queue stopped
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: changes
    facts:
    - Stopped
  contexts:
    web:
      place: web::fleet::print-farm
---

# Stop a printer's queue

## Trigger

A printer should finish its current job and then rest.

## Outcome

The current print continues; nothing else dispatches until Resume.
