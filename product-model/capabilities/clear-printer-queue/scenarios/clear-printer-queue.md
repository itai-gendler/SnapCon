---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Clear Queue on a printing printer and confirms
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
- text: The Product cancels the print on the printer
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Cancelled
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product records the running Queued job as cancelled, removes the waiting ones and leaves the Printer queue idle
  kind: product
  actor: regular-user
  entities:
  - entity: queued-job
    as: running
    effect: changes
    from: Printing
    to: Cancelled
    facts:
    - Finished at
  - entity: queued-job
    as: waiting
    effect: removes
    from: Queued
  - entity: printer-queue
    effect: changes
    from: Printing
    to: Idle
    facts:
    - Current job
    - Jobs waiting
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# Clear a printer's queue

## Trigger

A batch is called off.

## Outcome

The printer stops and its queue is empty; it cannot be undone.

## Edge cases

- If the printer cannot be told to cancel, nothing is cleared and the reason shows.
