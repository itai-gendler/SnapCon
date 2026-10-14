---
appliesTo:
- type: entity
  id: printer-queue
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
  target: queue/QueueStore.js
---

# A printer's queue is run by an Admin, a Regular user sharing one of the printer's groups, or SnapCon itself

Pausing, resuming, stopping, clearing, bed-clear confirmation and resolving attention follow the printer's access; dispatch and print tracking are SnapCon's own.
