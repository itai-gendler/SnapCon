---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Admin opens SnapCon for the first time
  kind: actor
  actor: admin
  entities: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
  capability: monitor-fleet
- text: No printer is configured, so the Product opens Settings at Printers
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
  capability: monitor-fleet
- text: The Admin chooses Discover and Scan
  kind: actor
  actor: admin
  entities: []
  contexts:
    web:
      place: web::settings::discover-printers
  capability: discover-printers
- text: The Product lists the supported printers it found
  kind: product
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
  capability: discover-printers
- text: The Admin chooses Add All & Save
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
  capability: add-printer
- text: The Product adds every found printer
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
  capability: add-printer
---

# Discover and add printers on first launch

## Trigger

SnapCon starts for the first time with no printers.

## Outcome

The discovered printers are configured and appear on the fleet dashboard.
