---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user sends files to a Printer pool
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  - entity: file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-queue
- text: A File is missing or cannot be printed, or the pool has no printer the person may use
  kind: condition
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-queue
- text: The Product refuses the whole request and queues nothing
  kind: product
  actor: regular-user
  entities: []
  contexts:
    web:
      place: web::fleet::send-to-queue
---

# Send to Queue refused

## Trigger

One selected file was deleted meanwhile.

## Outcome

No printer receives part of the batch.
