---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user opens Health and picks a printer
  kind: actor
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::printer-health
- text: The Product reads heaters, fans, controller, storage and faults from the printer and lists what needs attention with the service history
  kind: product
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Temperatures
    - Attention reasons
    - Total print hours
    - Warranty
    - Next maintenance
  - entity: maintenance-entry
    effect: reads
    facts:
    - Date
    - Component
  contexts:
    web:
      place: web::fleet::printer-health
---

# Open a printer's health page

## Trigger

A person suspects a printer is unwell.

## Outcome

The health page shows the printer's own readings; anything the printer does not report shows as unavailable.

## Edge cases

- Printers whose connector cannot report health are shown as not supported.
