---
appliesTo:
- type: entity
  id: printer
  effect: creates
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin adds a printer

Printers are added in Settings → Printers.
