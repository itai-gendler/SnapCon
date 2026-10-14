---
kind: edge
routes:
  web: Web
steps:
- text: A Printer queue's next Queued job is being sent
  kind: condition
  unattended: true
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Current job
  - entity: queued-job
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::print-farm
- text: The printer refuses or does not answer, so the Product marks the Queued job failed and the Printer queue as needing attention, and records the failure
  kind: product
  entities:
  - entity: printer
    effect: reads
    facts:
    - Online
  - entity: queued-job
    effect: changes
    from: Queued
    to: Failed
    facts:
    - Finished at
  - entity: printer-queue
    effect: changes
    from: Idle
    to: Needs attention
    facts:
    - Attention reason
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# Dispatch fails

## Trigger

The printer went offline in the moment its job was sent.

## Outcome

The queue needs attention: Retry job, Skip job or Stop Queue.
