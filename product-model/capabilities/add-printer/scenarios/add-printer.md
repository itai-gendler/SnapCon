---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Add in Printers, enters a name, picks the connector and enters the address, access code or token and the other details
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
- text: The Admin saves
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product adds the printer with a lasting identity, fills in the serial number from the printer when it can, and records the change
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: creates
    to: Idle
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
    - Position
  contexts:
    web:
      place: web::settings::printer-settings
---

# Add a printer by hand

## Trigger

A new printer joins the farm.

## Outcome

The printer appears on the fleet dashboard for the groups it is shared with, Everyone by default.

## Edge cases

- The brand comes from the connector; only generic Klipper printers take a typed brand.
- An address with a scheme, port or path in the IP field is refused.
