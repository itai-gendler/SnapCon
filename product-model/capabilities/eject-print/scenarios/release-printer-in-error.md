---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses a printer shown in error on the Print Farm view and confirms releasing it
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product ejects the stuck job on the printer
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Error
    to: Idle
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::print-farm
---

# Release a printer in error from the Print Farm view

## Trigger

A printer of a pool is stuck in error with a job.

## Outcome

The printer is free again for its queue.

## Edge cases

- A printer without an eject command keeps showing its last job until the next print starts.
