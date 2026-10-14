---
kind: primary
routes:
  web: Web
steps:
- text: The Admin drags a printer row, or chooses Move up or Move down, and saves
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
      place: web::settings::printer-settings
- text: The Product saves the new order
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: changes
    facts:
    - Position
  contexts:
    web:
      place: web::settings::printer-settings
---

# Reorder printers in Settings

## Trigger

An Admin tidies the printer list.

## Outcome

The fleet follows the new order.
