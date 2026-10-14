---
kind: primary
routes:
  web: Web
steps:
- text: Every five seconds, a Printer queue is idle, not paused or stopped, has a waiting job and its printer is free and online
  kind: condition
  unattended: true
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Paused
    - Stopped
    - Jobs waiting
  - entity: printer
    effect: reads
    facts:
    - Online
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product takes the first Queued job and fingerprints its File again
  kind: product
  entities:
  - entity: queued-job
    effect: changes
    from: Queued
    to: Dispatching
    facts: []
  - entity: printer-queue
    effect: changes
    from: Idle
    to: Dispatching
    facts:
    - Current job
    - Jobs waiting
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
  contexts:
    web:
      place: web::fleet::print-farm
- text: The fingerprint matches, so the Product sends the File unless the printer already has it, applies the head mapping and print options and starts the print
  kind: product
  entities:
  - entity: queued-job
    effect: reads
    facts:
    - Content fingerprint
    - Head mapping
    - Print options
  - entity: file
    effect: reads
    facts:
    - Name
  - entity: printer-file
    effect: creates
    to: Stored
    facts:
    - Name
    - Size
  - entity: printer
    effect: changes
    from: Idle
    to: Printing
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::print-farm
- text: The Product marks the Queued job and the Printer queue printing and records the start
  kind: product
  entities:
  - entity: queued-job
    effect: changes
    from: Dispatching
    to: Printing
    facts: []
  - entity: printer-queue
    effect: changes
    from: Dispatching
    to: Printing
    facts: []
  contexts:
    web:
      place: web::fleet::print-farm
---

# Dispatch the next job

## Trigger

A printer of a pool becomes free with work waiting.

## Outcome

The next job prints without anyone touching SnapCon.

## Edge cases

- A printer in maintenance, in error, or starting another print is not free.
- A job whose folder is unreachable keeps its place and waits for the folder to answer.
