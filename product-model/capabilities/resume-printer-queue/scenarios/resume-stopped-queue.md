---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Resume on a stopped Printer queue
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Stopped
  contexts:
    web:
      place: web::fleet::print-farm
- text: The printer is checked live and is no longer printing the Queued job
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Current print
  - entity: queued-job
    effect: reads
    facts:
    - File
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product clears the stop and, since the print's outcome is unknown, asks a person to decide before dispatching
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: changes
    from: Printing
    to: Needs attention
    facts:
    - Stopped
    - Attention reason
  contexts:
    web:
      place: web::fleet::print-farm
---

# Resume a stopped queue

## Trigger

A queue stopped while its job printed is restarted after the print ended unseen.

## Outcome

The queue offers Resume, Retry job, Skip job or Stop Queue instead of guessing what happened.
