---
kind: primary
routes:
  web: Web
steps:
- text: The Admin selects printers, chooses Edit tags and enters the tags
  kind: actor
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Tags
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product keeps up to 20 distinct tags of up to 24 characters on each printer
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: changes
    facts:
    - Tags
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Edit tags of selected printers

## Trigger

An Admin groups printers for filtering, for example by color or customer.

## Outcome

The printers carry the new tags and the tag filter offers them.
