---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Stop Queue on a Printer queue that needs attention
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
- text: The Product stops the queue and keeps the unresolved reason
  kind: product
  actor: regular-user
  entities:
  - entity: printer-queue
    effect: changes
    facts:
    - Stopped
  contexts:
    web:
      place: web::fleet::print-farm
---

# Stop a queue that needs attention

## Trigger

The operator cannot deal with a failure now.

## Outcome

The failure stays to be resolved, and the queue will not go on by itself afterwards.
