---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Online in Maintenance for a printer in maintenance
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::maintenance
- text: The Product ends maintenance and the printer shows its reported status again
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Maintenance
    to: Idle
    facts: []
  contexts:
    web:
      place: web::fleet::maintenance
---

# Bring a printer back online

## Trigger

The service is done.

## Outcome

The printer can print and dispatch again.
