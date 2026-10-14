---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Remove on a printer, confirms and saves
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::printer-settings
- text: The Product removes the printer and records the change
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: removes
    from: Idle
  contexts:
    web:
      place: web::settings::printer-settings
---

# Remove a printer

## Trigger

A printer leaves the farm.

## Outcome

It no longer appears anywhere; its history is kept for review.
