---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns off Enable Queue Management
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - Queue management
  contexts:
    web:
      place: web::settings::queue-management-settings
- text: The Product turns it off and stops dispatching from the queues
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - Queue management
  contexts:
    web:
      place: web::settings::queue-management-settings
---

# Turn off Queue Management

## Trigger

A farm goes back to sending files by hand.

## Outcome

Queues stop dispatching; pools and queued jobs are kept.
