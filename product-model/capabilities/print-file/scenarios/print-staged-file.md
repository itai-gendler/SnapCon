---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Print on a printer card that shows a Printer file ready to print
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
      place: web::fleet::fleet-dashboard
- text: The Product applies the head mapping and print options and starts the print without uploading again
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: changes
    from: Ready to print
    to: Stored
    facts: []
  - entity: printer
    effect: changes
    from: Idle
    to: Printing
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Print the file staged on a printer

## Trigger

A staged file's printer is ready.

## Outcome

The printer prints the staged file and the ready-to-print banner clears.
