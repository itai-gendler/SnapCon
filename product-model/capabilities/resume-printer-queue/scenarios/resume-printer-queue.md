---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Resume on a paused Printer queue
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Paused
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product clears the pause and dispatches the next job if the printer is free
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: changes
    facts:
    - Paused
  - entity: printer
    effect: reads
    facts:
    - Online
  contexts:
    web:
      place: web::fleet::print-farm
---

# Resume a paused queue

## Trigger

The reason to hold the queue is gone.

## Outcome

The queue dispatches again.
