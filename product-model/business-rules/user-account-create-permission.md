---
appliesTo:
- type: entity
  id: user-account
  effect: creates
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin creates a user account

Accounts are managed in Settings → Users.
