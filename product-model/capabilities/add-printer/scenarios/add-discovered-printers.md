---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Add on printers found by Discover, or Add All & Save on first setup
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Address
    - Brand
  contexts:
    web:
      place: web::settings::discover-printers
- text: The Product adds each one with what the printer reported about itself
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: creates
    to: Idle
    facts:
    - Name
    - Brand
    - Connector
    - Address
    - Serial number
    - Position
  contexts:
    web:
      place: web::settings::discover-printers
---

# Add discovered printers

## Trigger

A scan found the farm's printers.

## Outcome

The printers are configured without typing addresses.
