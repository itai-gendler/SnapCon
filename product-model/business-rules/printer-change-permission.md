---
appliesTo:
- type: entity
  id: printer
  effect: changes
permits:
- actors:
  - admin
- related:
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
  target: server.js
---

# A printer is operated by an Admin or a Regular user sharing one of its groups

Printing, pausing, resuming, cancelling, emergency stops, ejecting, heating, excluding objects and maintenance mode are for Admins and for Regular users whose groups may use the printer; View Only users only watch. SnapCon itself moves a printer when its queue dispatches and when it observes a print ending.
