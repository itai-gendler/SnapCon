---
appliesTo:
- type: entity
  id: printer
  effect: reads
permits:
- actors:
  - admin
- related:
  - verb: is-shared-with
    entity: group
  - verb: includes
    entity: regular-user
- related:
  - verb: is-shared-with
    entity: group
  - verb: includes
    entity: view-only-user
- actors:
  - slicer
- unattended: true
references:
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
- kind: code
  role: implementation
  target: server.js
---

# Only an Admin or a person sharing one of its groups sees a printer

Admins see every printer. Regular and View Only users see a printer only when one of their groups may use it; a printer or person without any group counts as Everyone. The slicer hook on the SnapCon machine names printers directly, and SnapCon itself watches every printer.
