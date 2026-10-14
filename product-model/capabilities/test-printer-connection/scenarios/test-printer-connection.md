---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Test connection on a printer row
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Address
    - Connector
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product contacts the printer and shows its state, bed temperature and firmware, or why it could not be reached
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Temperatures
    - Online
  contexts:
    web:
      place: web::settings::printer-settings
---

# Test a printer's connection

## Trigger

An Admin entered a new address.

## Outcome

The Admin knows whether the printer answers before saving.
