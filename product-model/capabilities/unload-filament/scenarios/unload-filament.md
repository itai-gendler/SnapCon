---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses unload on one or more toolheads of a printer
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  - entity: toolhead
    effect: reads
    facts:
    - Number
    - Filament color
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product tells the printer to unload them and records it
  kind: product
  actor: regular-user
  entities:
  - entity: toolhead
    effect: changes
    from: Loaded
    to: Empty
    facts: []
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Unload filament from toolheads

## Trigger

A spool must come out.

## Outcome

The printer unloads the filament; the toolheads show empty once the printer reports it.

## Edge cases

- Printers without filament unload do not offer it.
