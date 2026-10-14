---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user saves a Maintenance entry without a date
  kind: actor
  actor: regular-user
  entities:
  - entity: maintenance-entry
    effect: reads
    facts:
    - Component
  contexts:
    web:
      place: web::fleet::maintenance
- text: The Product refuses it
  kind: product
  actor: regular-user
  entities: []
  contexts:
    web:
      place: web::fleet::maintenance
---

# Service without a date refused

## Trigger

A person forgets the date.

## Outcome

Nothing is recorded.
