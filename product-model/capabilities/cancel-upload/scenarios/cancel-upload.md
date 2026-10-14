---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses Cancel upload on the upload strip of a printer card
  kind: actor
  actor: regular-user
  entities:
  - entity: printer-file
    effect: reads
    facts:
    - Name
    - Size
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The upload is still sending its last bytes
  kind: condition
  entities:
  - entity: printer-file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product stops the transfer and records the cancellation
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: removes
    from: Sending
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Cancel an upload

## Trigger

A person sent the wrong file.

## Outcome

The transfer stops; no print starts.

## Edge cases

- Once the last byte is written the upload can no longer be cancelled.
