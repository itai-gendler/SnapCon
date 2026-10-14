---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user asks for a bed temperature above the printer's maximum
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::heat-printers
- text: The temperature is outside 0 to 120 °C or above the printer's own maximum
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::heat-printers
- text: The Product refuses it and the bed target stays as it was
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::heat-printers
---

# Bed temperature out of range

## Trigger

A person types a temperature the printer cannot take.

## Outcome

Nothing changes on the printer.
