---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user types a name, status, color family or a progress filter such as >75% and picks a tag or status tab
  kind: actor
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Tags
    - Current print
  - entity: toolhead
    effect: reads
    facts:
    - Filament color
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product shows only the printers that match, sorted by status, time remaining or name, or in the fleet's own order
  kind: product
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Tags
    - Current print
    - Position
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Search, filter and sort the fleet

## Trigger

A person looks for particular printers in a large farm.

## Outcome

Only matching printers show; the choice of view and sort is remembered in that browser.
