---
kind: primary
routes:
  web: Web
steps:
- text: The Admin drags a printer card by its status badge to a new place while No Sort is on
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Position
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product saves the new order for everyone
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: changes
    facts:
    - Position
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Drag a printer card

## Trigger

An Admin wants the cards in the order the printers stand.

## Outcome

Every person sees the printers in the new order when No Sort is chosen.
