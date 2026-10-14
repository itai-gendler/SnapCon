---
appliesTo:
- type: entity
  id: printer-file
  effect: changes
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
---

# A file on a printer is moved on by an Admin, a Regular user sharing one of its groups, the slicer hook or SnapCon itself

Staging, printing and ejecting a staged file follow the printer's access; a held file is sent by SnapCon once the printer is free, on behalf of whoever sent it.
