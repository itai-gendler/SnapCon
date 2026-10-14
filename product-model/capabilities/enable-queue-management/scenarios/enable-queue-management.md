---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns on Enable Queue Management
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
- text: The Product turns it on, creates the Unassigned Printer pool when missing and puts every printer without a pool in it
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - Queue management
  - entity: printer-pool
    effect: creates
    facts:
    - Name
    - Bed clear
    - Auto-balance
    - Built-in
  - entity: printer
    effect: changes
    facts:
    - Printer pool
  contexts:
    web:
      place: web::settings::queue-management-settings
---

# Turn on Queue Management

## Trigger

A farm starts working through queues.

## Outcome

The Print Farm view and Send to Queue are available.
