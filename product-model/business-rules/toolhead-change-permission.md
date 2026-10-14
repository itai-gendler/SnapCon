---
appliesTo:
- type: entity
  id: toolhead
  effect: changes
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

# Toolhead filament is changed by an Admin or a Regular user sharing one of the printer's groups

Unloading filament and relabeling a toolhead's color follow the printer's own access.
