---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects files in the file list and chooses Send to Queue
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-queue
- text: The Regular user picks a Printer pool, the copies of each File and Print on All, and checks the preview
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  - entity: printer
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
- text: The Product checks every File, notes its content fingerprint and adds the copies of every File to each Printer queue of the pool the person may use
  kind: product
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
  - entity: queued-job
    effect: creates
    to: Queued
    facts:
    - File
    - Content fingerprint
    - Head mapping
    - Print options
    - Queued by
    - Queued at
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
  contexts:
    web:
      place: web::fleet::send-to-queue
---

# Send to a pool with Print on All

## Trigger

One of each part is wanted from every printer of a pool.

## Outcome

Every printer of the pool has the jobs at the end of its queue and dispatches them in turn.
