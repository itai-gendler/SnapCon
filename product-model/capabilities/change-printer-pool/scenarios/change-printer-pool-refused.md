---
kind: validation
routes:
  web: Web
steps:
- text: The Admin picks another Printer pool for a printer
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  - entity: printer-pool
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Printer queue still has jobs or is printing, or the printer prints only some kinds of sliced output
  kind: condition
  actor: admin
  entities:
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
  - entity: printer
    effect: reads
    facts:
    - Connector
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product refuses and says to clear the queue first, or that the printer cannot join a pool yet
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::printer-settings
---

# Pool change refused

## Trigger

A busy printer is moved.

## Outcome

The printer stays where it was.
