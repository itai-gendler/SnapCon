---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Cancel on a printer card
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
- text: The Product sends Cancel to the printer and records it in the activity log
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Cancelled
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Cancel print

## Trigger

A person decides to cancel a print.

## Outcome

The print is cancelled on the printer.
