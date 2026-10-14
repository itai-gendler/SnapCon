---
kind: edge
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
- text: The Product starts sending it
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: creates
    to: Sending
    facts:
    - Name
    - Size
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The printer stops answering, refuses the File, or the G-code folder becomes unreachable
  kind: condition
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Online
  - entity: file
    effect: reads
    facts: []
  - entity: folder
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Product marks the upload failed with the reason and the percentage it reached
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: changes
    from: Sending
    to: Upload failed
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
---

# Upload fails midway

## Trigger

The network drops during a long transfer.

## Outcome

The card says the upload failed and why; nothing is printed.
