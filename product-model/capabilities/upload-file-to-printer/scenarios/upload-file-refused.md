---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user uploads a File to a printer
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The printer cannot print this kind of file, is printing a file of the same name, is in maintenance, or already has a different file of that name while Overwrite different files is off
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Connector
    - Current print
  - entity: settings
    effect: reads
    facts:
    - Overwrite different files
  - entity: file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Product refuses before sending anything and says why
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
---

# Upload refused

## Trigger

A person sends a file the printer must not receive.

## Outcome

Nothing is sent; the running print is never overwritten.

## Edge cases

- A Bambu Lab printer takes only sliced .3mf projects and G-code its firmware runs.
- A file sliced for another printer model is sent only after the person confirms.
