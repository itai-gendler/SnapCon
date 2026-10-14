---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user expands a printer on the Print Farm view and removes a waiting Queued job
  kind: actor
  actor: regular-user
  entities:
  - entity: queued-job
    effect: reads
    facts:
    - File
    - Queued by
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product removes it and lists it as removed in the Printer queue's recent history
  kind: product
  actor: regular-user
  entities:
  - entity: queued-job
    effect: removes
    from: Queued
  - entity: printer-queue
    effect: changes
    facts:
    - Jobs waiting
    - Recent history
  contexts:
    web:
      place: web::fleet::print-farm
---

# Remove a waiting job

## Trigger

A job is no longer wanted.

## Outcome

The job will not print.
