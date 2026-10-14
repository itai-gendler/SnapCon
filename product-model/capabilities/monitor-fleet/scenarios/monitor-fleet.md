---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user opens SnapCon
  kind: actor
  actor: view-only-user
  entities: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product checks every printer the person may see at the refresh interval and shows each one's status, current print, temperatures and toolhead filament
  kind: product
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Current print
    - Temperatures
    - Online
    - Last seen
  - entity: toolhead
    effect: reads
    facts:
    - Number
    - Filament color
    - Material
  - entity: settings
    effect: reads
    facts:
    - Refresh interval
    - Default view
    - Toolhead notation
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product marks printers whose maintenance is due or whose queue needs attention
  kind: product
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Attention reasons
  - entity: printer-queue
    effect: reads
    facts:
    - Jobs waiting
    - Paused
    - Stopped
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Watch the fleet

## Trigger

A person wants to know what the farm is doing.

## Outcome

The dashboard shows only the printers whose groups the person shares, in the default view.

## Edge cases

- A printer that does not answer shows as offline with when it was last seen and is checked again every ten seconds.
- An empty toolhead shows as an empty slot, never as a spool.
- Opening /orca/<printer name> shows that one printer only.
