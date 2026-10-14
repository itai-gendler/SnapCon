---
kind: edge
routes:
  web: Web
steps:
- text: SnapCon starts again while a Printer queue was dispatching
  kind: condition
  unattended: true
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Current job
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product checks the printer live and asks a person to decide when the outcome is unknown or the printer prints something else
  kind: product
  entities:
  - entity: printer
    effect: reads
    facts:
    - Current print
  - entity: printer-queue
    effect: changes
    from: Dispatching
    to: Needs attention
    facts:
    - Attention reason
  contexts:
    web:
      place: web::fleet::print-farm
---

# Dispatch interrupted by a restart

## Trigger

SnapCon restarted in the middle of a dispatch.

## Outcome

No job is sent twice; a person decides how to go on.

## Edge cases

- A printer still printing the job it was sent simply carries on printing it.
