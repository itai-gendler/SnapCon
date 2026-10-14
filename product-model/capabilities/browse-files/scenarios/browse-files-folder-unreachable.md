---
kind: edge
routes:
  web: Web
steps:
- text: The View-only user opens the file list
  kind: actor
  actor: view-only-user
  entities:
  - entity: file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::files
- text: The G-code folder, for example on a network share, does not answer
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - G-code folder
  - entity: folder
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::files
- text: The Product says the G-code folder is unreachable and keeps checking, without slowing the rest of SnapCon
  kind: product
  actor: view-only-user
  entities:
  - entity: folder
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::files
---

# G-code folder unreachable

## Trigger

The network share holding the G-code folder is down.

## Outcome

The file list explains the outage and recovers when the share answers again.
