---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects several printers in the List view and chooses Pause
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product pauses each selected printer that is printing and reports how many paused, failed or were not eligible
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Paused
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Pause several prints

## Trigger

A person needs to stop part of the farm for a moment.

## Outcome

Every printing printer of the selection is paused; the others are counted as not eligible.
