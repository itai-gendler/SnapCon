---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Resume on a Printer queue that needs attention because its print failed
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
- text: The printer is checked live and is paused
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product resumes the printer and the Printer queue goes back to printing the same queued job
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Paused
    to: Printing
    facts:
    - Current print
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Printing
    facts:
    - Attention reason
  - entity: queued-job
    effect: changes
    from: Failed
    to: Printing
    facts: []
  contexts:
    web:
      place: web::fleet::print-farm
---

# Resume a queued print that paused

## Trigger

A queued print paused, for example on a filament runout, and the operator fixed it.

## Outcome

The print continues and the queue follows it again.

## Edge cases

- A printer that is no longer paused is refused with the reason that it is not in a resumable state.
