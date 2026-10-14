---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Skip job on a Printer queue whose print failed
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Attention reason
    - Current job
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product marks the Queued job skipped and waits for the bed to be cleared
  kind: product
  actor: regular-user
  entities:
  - entity: queued-job
    effect: changes
    from: Failed
    to: Skipped
    facts:
    - Finished at
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Awaiting bed clear
    facts:
    - Attention reason
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# Skip a failed print

## Trigger

A failed job is not worth printing again.

## Outcome

The queue goes on with the next job once the bed is clear.
