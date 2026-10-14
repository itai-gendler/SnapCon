---
kind: primary
routes:
  web: Web
steps:
- text: The Admin checks a Group under Access on a printer and saves
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
- text: The Product adds the Group to the printer's groups
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

# Give a group access to a printer

## Trigger

A printer is reserved for one team.

## Outcome

Regular and View Only users of that group see and use the printer; once a printer has groups, Everyone no longer applies to it.
