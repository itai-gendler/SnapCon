---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Skip job on a Printer queue whose File is missing
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Attention reason
  - entity: file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product marks the Queued job skipped and goes back to idle without a bed clear
  kind: product
  actor: regular-user
  entities:
  - entity: queued-job
    effect: changes
    from: Dispatching
    to: Skipped
    facts:
    - Finished at
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Idle
    facts:
    - Attention reason
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# Skip a job whose file is missing

## Trigger

The file of a waiting job was deleted on purpose.

## Outcome

The next job dispatches.
