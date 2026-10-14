---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Eject on a printer that shows its finished job
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
- text: The Product clears the job on the printer and any staged Printer file stops being offered as ready to print
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Complete
    to: Idle
    facts:
    - Current print
  - entity: printer-file
    effect: changes
    from: Ready to print
    to: Stored
    facts: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Eject a finished job

## Trigger

The part was removed and the operator wants the card to read idle.

## Outcome

The printer reads idle and holds no job for SnapCon.
