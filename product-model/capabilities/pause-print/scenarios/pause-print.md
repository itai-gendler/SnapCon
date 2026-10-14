---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Pause on a printer card
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product sends Pause to the printer and records it in the activity log
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Paused
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Pause print

## Trigger

A person decides to pause a print.

## Outcome

The printer pauses; the print can be resumed.
