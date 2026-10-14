---
appliesTo:
- type: entity
  id: queued-job
  effect: removes
permits:
- actors:
  - admin
- related:
  - verb: holds
    entity: printer-queue
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

# Queued jobs are removed by an Admin or a Regular user sharing one of the printer's groups

Removing a waiting job, clearing a queue and acknowledging a recovery follow the printer's access.
