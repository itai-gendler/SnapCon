---
kind: edge
routes:
  web: Web
steps:
- text: Every 30 seconds, a printer whose Printer queue is printing now reports an error or a cancelled print
  kind: condition
  unattended: true
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Current job
  - entity: printer
    effect: reads
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product marks the Queued job failed, the Printer queue as needing attention, and records the reason the printer gave
  kind: product
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Error
    facts: []
  - entity: queued-job
    effect: changes
    from: Printing
    to: Failed
    facts:
    - Finished at
  - entity: printer-queue
    effect: changes
    from: Printing
    to: Needs attention
    facts:
    - Attention reason
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# A queued print fails

## Trigger

A queued print fails or is cancelled at the machine.

## Outcome

The queue stops dispatching that printer until a person resumes, retries, skips or stops it.
