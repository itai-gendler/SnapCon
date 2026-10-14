---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Retry job on a Printer queue whose print failed
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
- text: The Product adds a copy of the failed Queued job at the front and waits for the bed to be cleared
  kind: product
  actor: regular-user
  entities:
  - entity: queued-job
    as: retry
    effect: creates
    to: Queued
    facts:
    - File
    - Content fingerprint
    - Head mapping
    - Print options
    - Queued by
    - Queued at
    - Retry of
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Awaiting bed clear
    facts:
    - Attention reason
    - Jobs waiting
  contexts:
    web:
      place: web::fleet::print-farm
---

# Retry a failed print

## Trigger

A print failed for a reason that is now fixed.

## Outcome

After the bed is confirmed clear, the retry prints first.
