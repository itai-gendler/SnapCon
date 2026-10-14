---
kind: primary
routes:
  web: Web
steps:
- text: Every five seconds, a Printer pool has Auto-balance on and one of its printers is idle with an empty Printer queue
  kind: condition
  unattended: true
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Auto-balance
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product moves the oldest waiting Queued job of the printer of the same connector with the longest queue to the idle one and records the move
  kind: product
  entities:
  - entity: printer
    effect: reads
    facts:
    - Connector
  - entity: queued-job
    effect: changes
    facts: []
  - entity: printer-queue
    effect: changes
    facts:
    - Jobs waiting
  contexts:
    web:
      place: web::fleet::print-farm
---

# Move a job to an idle printer

## Trigger

A printer of a pool ran out of work while another has a backlog.

## Outcome

The idle printer gets a job and dispatches it.
