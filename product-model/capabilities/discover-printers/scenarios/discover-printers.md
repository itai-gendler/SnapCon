---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Discover and Scan for the local network or a subnet
  kind: actor
  actor: admin
  entities: []
  contexts:
    web:
      place: web::settings::discover-printers
- text: The Product probes every address of the chosen subnets for supported printers and lists what it found, marking printers already added
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Address
    - Brand
  contexts:
    web:
      place: web::settings::discover-printers
---

# Scan the network for printers

## Trigger

An Admin sets up several printers at once.

## Outcome

Found printers show with an Add button; a /24 scan takes about ten seconds.

## Edge cases

- A custom range larger than /20 is refused.
