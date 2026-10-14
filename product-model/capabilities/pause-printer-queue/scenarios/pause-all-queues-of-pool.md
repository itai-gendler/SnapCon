---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Pause All Queues on a Printer pool
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product pauses each Printer queue of the pool
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

# Pause every queue of a pool

## Trigger

A pool's material runs low.

## Outcome

No printer of the pool takes a next job.
