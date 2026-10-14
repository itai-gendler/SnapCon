---
kind: primary
routes:
  web: Web
steps:
- text: Every 30 seconds, a printer whose Printer queue is printing now reports its print complete
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
- text: The Product marks the Queued job completed and waits for its bed to be cleared
  kind: product
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Complete
    facts: []
  - entity: queued-job
    effect: changes
    from: Printing
    to: Completed
    facts:
    - Finished at
  - entity: printer-queue
    effect: changes
    from: Printing
    to: Awaiting bed clear
    facts:
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# A queued print finishes

## Trigger

A queued print ends.

## Outcome

The Print Farm view shows the printer awaiting bed clear.
