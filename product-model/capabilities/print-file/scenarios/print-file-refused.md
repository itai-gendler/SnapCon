---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user chooses Print for a printer
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The printer is in maintenance, already printing the same one, or cannot print its kind
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Connector
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product refuses and says why
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Print refused

## Trigger

A person starts a print the printer must not take.

## Outcome

Nothing starts.
