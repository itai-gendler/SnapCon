---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Pause on a printer of the Print Farm view
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
- text: The Product marks the Printer queue paused
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: changes
    facts:
    - Paused
  contexts:
    web:
      place: web::fleet::print-farm
---

# Pause a printer's queue

## Trigger

The operator wants a printer to stop taking new jobs for now.

## Outcome

The current print continues; no next job dispatches until the queue is resumed.
