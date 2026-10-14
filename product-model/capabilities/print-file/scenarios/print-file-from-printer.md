---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user opens Print from printer, picks a stored Printer file and confirms
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
    - Colors
    - Estimated time
  contexts:
    web:
      place: web::fleet::printer-files
- text: The Product starts it on the printer and records the print start
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: reads
    facts:
    - Name
  - entity: printer
    effect: changes
    from: Complete
    to: Printing
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::printer-files
---

# Print a file already on the printer

## Trigger

A file sent earlier, or from the printer's own slicer, should print again.

## Outcome

The printer prints the chosen file.

## Edge cases

- Reprint on a card starts the printer's last file the same way.
