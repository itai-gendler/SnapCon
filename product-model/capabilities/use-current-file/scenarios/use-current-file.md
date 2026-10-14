---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Use current file on a Printer queue whose File changed
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
- text: The Product fingerprints the File afresh, keeps the original fingerprint and who accepted the change, and puts the Queued job back at the front
  kind: product
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
  - entity: queued-job
    effect: changes
    from: Dispatching
    to: Queued
    facts:
    - Content fingerprint
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Idle
    facts:
    - Attention reason
  contexts:
    web:
      place: web::fleet::print-farm
---

# Accept a changed file

## Trigger

The part was re-sliced on purpose after it was queued.

## Outcome

The job prints the current file.
