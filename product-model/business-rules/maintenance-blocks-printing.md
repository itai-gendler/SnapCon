---
appliesTo:
- type: capability
  id: print-file
- type: capability
  id: dispatch-queued-job
- type: entity
  id: printer
  effect: changes
  from: Maintenance
  to: Printing
references:
- kind: code
  role: implementation
  target: server.js
---

# Nothing is printed or dispatched on a printer in maintenance

Printing is refused with the reason, and the printer's queue does not dispatch until it is brought back online.
