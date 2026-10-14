---
appliesTo:
- type: entity
  id: printer-pool
  effect: creates
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin creates a Printer pool

Pools are managed in Settings → Queue Management.
