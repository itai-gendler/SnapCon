---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Users

Settings → Users: User Access Management, user accounts, groups and one-time code delivery.

## Boundary

Users owns accounts, roles, groups and sign-in settings. It does not own signing in itself or which printers a group is given.
