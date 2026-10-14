---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Acknowledge & resume on a Printer queue that found an unexpected print
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Attention reason
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product drops the Queued job it was dispatching and sets the Printer queue idle without touching the machine
  kind: product
  actor: regular-user
  entities:
  - entity: queued-job
    effect: removes
    from: Dispatching
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Idle
    facts:
    - Attention reason
    - Current job
  contexts:
    web:
      place: web::fleet::print-farm
---

# Acknowledge and resume

## Trigger

Someone started a print by hand while SnapCon was restarting.

## Outcome

The queue trusts the printer and continues once it is free.
