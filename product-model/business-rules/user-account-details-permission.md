---
appliesTo:
- type: entity
  id: user-account
  effect: changes
  facts:
  - First name
  - Last name
  - Login name
  - Email
  - Phone
  - Role
  - One-time code sign-in
  - Password
  - Groups
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin changes a person's identity, role, sign-in method or groups

Names, login name, contact details, role, sign-in method, password and groups are set in Settings → Users.
