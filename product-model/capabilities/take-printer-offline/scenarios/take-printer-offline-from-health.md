---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user turns on the offline switch on a printer's health page
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::printer-health
- text: The Product puts the printer in maintenance
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Idle
    to: Maintenance
    facts: []
  contexts:
    web:
      place: web::fleet::printer-health
---

# Take a printer offline from its health page

## Trigger

Diagnostics show the printer needs service.

## Outcome

The printer shows Maintenance.
