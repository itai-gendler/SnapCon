---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Resume on a printer card
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
- text: The Product sends Resume to the printer and records it in the activity log
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Paused
    to: Printing
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Resume print

## Trigger

A person decides to resume a print.

## Outcome

The printer continues the print.
