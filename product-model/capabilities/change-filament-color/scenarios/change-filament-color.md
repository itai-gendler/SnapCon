---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user picks a new color and material for a toolhead on a printer card
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
    - Material
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product stores them on the printer and shows the color the printer actually applied
  kind: product
  actor: regular-user
  entities:
  - entity: toolhead
    effect: changes
    facts:
    - Filament color
    - Material
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Relabel a toolhead's filament

## Trigger

The filament loaded at the machine differs from what the printer thinks.

## Outcome

The toolhead shows the new color and material.

## Edge cases

- A printer with a fixed palette snaps the color to its nearest entry, and SnapCon shows that.
- A material must be one of the printer's own materials.
