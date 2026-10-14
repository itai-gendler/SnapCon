---
kind: primary
routes:
  web: Web
steps:
- text: The Admin unchecks a Group under Access on a printer and saves
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Groups with access
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product removes the Group from the printer's groups
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: changes
    facts:
    - Groups with access
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::printer-settings
---

# Take a group's access away

## Trigger

A team no longer uses a printer.

## Outcome

The group's members stop seeing the printer; a printer left with no group is shared with Everyone again.
