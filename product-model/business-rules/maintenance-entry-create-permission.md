---
appliesTo:
- type: entity
  id: maintenance-entry
  effect: creates
permits:
- actors:
  - admin
- related:
  - verb: has
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

# Maintenance is logged by an Admin or a Regular user sharing one of the printer's groups

View Only users see maintenance history but do not log it.
