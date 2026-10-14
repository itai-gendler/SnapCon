---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user opens Plate on a printing printer and selects objects on the map or in the list
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Plate objects
  contexts:
    web:
      place: web::fleet::plate
- text: The Regular user chooses Exclude
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Plate objects
  contexts:
    web:
      place: web::fleet::plate
- text: The Product sends an exclusion for each selected object, one at a time, and records each
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    facts:
    - Plate objects
  contexts:
    web:
      place: web::fleet::plate
---

# Exclude objects mid-print

## Trigger

One part of a plate failed and would waste filament or spoil the rest.

## Outcome

The excluded objects are marked Skipped for the rest of the print; there is no undo.

## Edge cases

- Plate shows only while a print with more than one object is printing or paused, on printers that support exclusion.
- An already excluded object cannot be selected again.
