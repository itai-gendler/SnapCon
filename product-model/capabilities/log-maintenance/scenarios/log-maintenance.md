---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user opens Maintenance for a printer, picks a component, date and reminder, adds part, notes and cost and saves
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Total print hours
  - entity: maintenance-entry
    effect: reads
    facts:
    - Date
    - Component
    - Part
    - Notes
    - Cost
    - Reminder
  contexts:
    web:
      place: web::fleet::maintenance
- text: The Product records the Maintenance entry with the printer's print hours and the next due date the reminder sets
  kind: product
  actor: regular-user
  entities:
  - entity: maintenance-entry
    effect: creates
    facts:
    - Date
    - Component
    - Part
    - Notes
    - Cost
    - Print hours
    - Reminder
    - Next due
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::maintenance
- text: The Product updates the printer's next maintenance and warranty
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Next maintenance
    - Warranty
  contexts:
    web:
      place: web::fleet::maintenance
---

# Log a service

## Trigger

A nozzle was replaced.

## Outcome

The history shows the service and, with a reminder, the printer shows when it is due next.

## Edge cases

- Picking a known component suggests its usual reminder, for example monthly for a nozzle and quarterly for a timing belt.
- A component typed for the first time is offered for later entries.
- Hour-based reminders are shown but cannot be chosen yet.
