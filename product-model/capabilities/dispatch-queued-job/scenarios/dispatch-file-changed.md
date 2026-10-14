---
kind: edge
routes:
  web: Web
steps:
- text: A Printer queue's next Queued job is taken for dispatch
  kind: condition
  unattended: true
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
  - entity: queued-job
    effect: reads
    facts:
    - File
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product finds the File's content differs from its fingerprint and asks a person to decide, sending nothing
  kind: product
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
  - entity: queued-job
    effect: changes
    from: Queued
    to: Dispatching
    facts: []
  - entity: printer-queue
    effect: changes
    from: Idle
    to: Needs attention
    facts:
    - Attention reason
    - Current job
  contexts:
    web:
      place: web::fleet::print-farm
---

# Queued file changed

## Trigger

A file was re-sliced or replaced after it was queued.

## Outcome

The queue needs attention: Use current file, Skip job or Stop Queue.

## Edge cases

- A file that is gone stops the queue the same way, for a missing file: Skip job or Stop Queue.
