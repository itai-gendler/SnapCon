---
appliesTo:
- type: entity
  id: user-account
  effect: removes
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin deletes a user account

Accounts are managed in Settings → Users.
