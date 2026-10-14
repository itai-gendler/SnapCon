---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects a Printer file in Print from printer, chooses Delete and confirms
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  - entity: printer-file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::printer-files
- text: The printer answers and the Printer file is not in use
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Online
  - entity: printer-file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::printer-files
- text: The Product deletes it from the printer and records it
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: removes
    from: Stored
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::printer-files
---

# Delete a file from a printer

## Trigger

A printer's storage fills up with old files.

## Outcome

The file is gone from the printer; a staged file deleted this way is no longer offered as ready to print.
