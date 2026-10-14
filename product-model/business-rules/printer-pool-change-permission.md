---
appliesTo:
- type: entity
  id: printer-pool
  effect: changes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin changes a Printer pool

Renaming a pool and switching its auto-balance are Admin actions, also on the Print Farm view.
