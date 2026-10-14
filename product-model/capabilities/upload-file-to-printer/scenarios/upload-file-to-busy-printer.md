---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user uploads a File to a printer that is printing
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
- text: Upload while printing is off
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - Upload while printing
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Product holds the File and shows it as queued on the printer card
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: creates
    to: Waiting for printer
    facts:
    - Name
  - entity: printer
    effect: reads
    facts:
    - Name
  - entity: file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: Once the printer is idle the Product sends it, applies the head mapping and stages it as ready to print
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: changes
    from: Waiting for printer
    to: Ready to print
    facts:
    - Size
    - Colors
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
---

# Upload waits for a busy printer

## Trigger

A person queues a file for a printer still finishing another job.

## Outcome

The file lands on the printer as soon as it is free, with no browser needed in the meantime.
