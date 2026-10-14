---
appliesTo:
- type: entity
  id: queued-job
  effect: creates
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

# Jobs are queued by an Admin or a Regular user sharing one of the printer's groups

Send to Queue reaches only the printers of the pool the person may use; retries follow the same access.
