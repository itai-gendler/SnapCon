---
appliesTo:
- type: entity
  id: printer
  effect: removes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin removes a printer

Printers are removed in Settings → Printers.
