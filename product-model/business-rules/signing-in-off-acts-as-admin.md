---
appliesTo:
- type: entity
  id: settings
  facts:
  - User access management
- type: capability
  id: sign-in
references:
- kind: code
  role: implementation
  target: auth.js#makeAuthMiddleware
- kind: doc
  role: intent
  target: README.md
---

# Without User Access Management everyone acts as an Admin

While User Access Management is off, nobody signs in and every visitor has the Admin's access; actions are recorded without a user. Roles, groups and one-time codes apply only while it is on.
