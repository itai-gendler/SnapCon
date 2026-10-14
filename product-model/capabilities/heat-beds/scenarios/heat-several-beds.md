---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user opens Heat printers, selects online printers, enters a bed temperature, turns on Staggered heating with a number of seconds and chooses Heat
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Online
    - Temperatures
  contexts:
    web:
      place: web::fleet::heat-printers
- text: The Product sets each printer's bed target in turn, the given seconds after the previous one, and shows each result
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    facts:
    - Temperatures
  contexts:
    web:
      place: web::fleet::heat-printers
---

# Heat several printers, staggered

## Trigger

The farm is about to start a batch and the beds must warm up.

## Outcome

Every selected bed heats toward the target; closing the dialog stops the printers not yet started.

## Edge cases

- Busy printers cannot be selected.
- Temperature 0 turns the bed heater off.
