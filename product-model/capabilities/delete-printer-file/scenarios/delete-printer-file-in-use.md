---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user chooses Delete on a Printer file
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::printer-files
- text: The printer is starting a print, printing it, still receiving it, or it waits in the Printer queue, or the printer cannot be reached
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Online
    - Current print
  - entity: printer-queue
    effect: reads
    facts:
    - Current job
  contexts:
    web:
      place: web::fleet::printer-files
- text: The Product refuses and says what still needs the Printer file
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::printer-files
---

# Deleting a file in use refused

## Trigger

A person tries to delete a file that is about to print or printing.

## Outcome

The file stays; deletion is permanent, so any doubt refuses.
