---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Preheat on a printer card and picks a temperature
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Temperatures
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product sets the printer's bed target and records it
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    facts:
    - Temperatures
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Preheat one printer

## Trigger

One printer is about to print.

## Outcome

The bed heats toward the target.
