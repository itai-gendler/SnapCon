---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects several printers in the Camera view, chooses Cancel and confirms
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
- text: The Product cancels each selected printer that is printing or paused
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Paused
    to: Cancelled
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Cancel several prints

## Trigger

A batch went wrong across several printers.

## Outcome

Every printing or paused printer of the selection is cancelled; the rest are counted as not eligible.
