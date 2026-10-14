---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Offline in Maintenance for an idle printer
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
- text: The Product puts the printer in maintenance and shows it so everywhere
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
      place: web::fleet::maintenance
---

# Take a printer offline

## Trigger

A printer is about to be serviced.

## Outcome

The printer shows Maintenance; printing on it is refused and its queue does not dispatch.
