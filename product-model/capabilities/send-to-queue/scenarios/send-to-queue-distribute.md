---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects files, chooses Send to Queue, a Printer pool, 12 copies and Distribute
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-queue
- text: The Product spreads the jobs round-robin across the pool's printers the person may use
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts: []
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

# Send to a pool with Distribute

## Trigger

A batch of identical parts should finish as soon as possible.

## Outcome

Twelve copies across four printers become three jobs each.
