---
appliesTo:
- type: capability
  id: delete-printer-pool
  contexts:
  - place: web::settings
references:
- kind: code
  role: implementation
  target: server.js
---

# A Printer pool with printers is never deleted

Its printers are reassigned first; Unassigned is built in.
