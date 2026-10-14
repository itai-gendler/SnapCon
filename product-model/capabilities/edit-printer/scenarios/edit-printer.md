---
kind: primary
routes:
  web: Web
steps:
- text: The Admin expands a printer in Printers, changes its details and saves
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Location
    - Brand
    - Connector
    - Address
    - Serial number
    - Purchase date
    - Power draw
    - Print defaults
    - Force default behavior
    - Tags
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product saves them, keeping the printer's identity, credentials left blank and its history
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: changes
    facts:
    - Name
    - Location
    - Brand
    - Connector
    - Address
    - Credentials
    - Serial number
    - Purchase date
    - Power draw
    - Print defaults
    - Force default behavior
    - Tags
  contexts:
    web:
      place: web::settings::printer-settings
---

# Edit a printer

## Trigger

A printer moved to another address or was renamed.

## Outcome

The printer keeps its maintenance history, queue and activity log under the new details.

## Edge cases

- A stored access code or token is never shown back; Replace sets a new one and Clear removes it.
