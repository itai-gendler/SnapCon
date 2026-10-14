---
appliesTo:
- type: entity
  id: printer-file
  effect: creates
permits:
- actors:
  - admin
- related:
  - verb: stores
    entity: printer
  - verb: is-shared-with
    entity: group
  - verb: includes
    entity: regular-user
- actors:
  - slicer
- unattended: true
references:
- kind: code
  role: implementation
  target: auth.js#requireRegular
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
- kind: code
  role: implementation
  target: notifyToken.js
---

# Files are sent to a printer by an Admin, a Regular user sharing one of its groups, or the slicer hook

Uploads and prints from SnapCon follow the printer's access; the slicer hook runs on the SnapCon machine itself. SnapCon itself places the files of queued jobs it dispatches.
