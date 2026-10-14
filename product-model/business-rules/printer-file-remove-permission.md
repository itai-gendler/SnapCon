---
appliesTo:
- type: entity
  id: printer-file
  effect: removes
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
references:
- kind: code
  role: implementation
  target: auth.js#requireRegular
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
---

# A file on a printer is deleted or its upload cancelled by an Admin or a Regular user sharing one of the printer's groups

View Only users cannot cancel uploads or delete files.
