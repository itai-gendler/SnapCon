---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user removes the finished part and chooses Bed clear, print next on the printer
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Current job
    - Jobs waiting
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product records who confirmed and sets the Printer queue idle
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: changes
    from: Awaiting bed clear
    to: Idle
    facts:
    - Current job
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product dispatches the next job when one waits and the queue is not paused
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
    - Paused
  contexts:
    web:
      place: web::fleet::print-farm
---

# Clear the bed and print next

## Trigger

A queued print finished and the part was taken off.

## Outcome

The next job starts, or the printer waits idle when none is left.
