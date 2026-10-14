---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Retry job on a Printer queue whose dispatch failed
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
- text: The Product adds a copy of the Queued job at the front and goes back to idle without a bed clear, since nothing printed
  kind: product
  actor: regular-user
  entities:
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
    - Retry of
  - entity: printer-queue
    effect: changes
    from: Needs attention
    to: Idle
    facts:
    - Attention reason
    - Jobs waiting
  contexts:
    web:
      place: web::fleet::print-farm
---

# Retry a job whose dispatch failed

## Trigger

The printer was unreachable when its job was sent.

## Outcome

The job is tried again on the next dispatch.
