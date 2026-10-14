---
appliesTo:
- type: entity
  id: queued-job
  effect: changes
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
- unattended: true
references:
- kind: code
  role: implementation
  target: auth.js#requireRegular
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
---

# Queued jobs are moved on by an Admin, a Regular user sharing one of the printer's groups, or SnapCon itself

Dispatching, completing and balancing are SnapCon's own; skipping, accepting a changed file and clearing follow the printer's access.
