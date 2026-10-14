---
appliesTo:
- type: entity
  id: group
  effect: creates
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin creates a group

Groups are managed in Settings → Users.
