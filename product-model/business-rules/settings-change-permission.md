---
appliesTo:
- type: entity
  id: settings
  effect: changes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin changes SnapCon settings

Every setting is changed in the Settings area.
