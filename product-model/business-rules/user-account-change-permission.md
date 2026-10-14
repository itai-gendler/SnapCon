---
appliesTo:
- type: entity
  id: user-account
  effect: changes
permits:
- actors:
  - admin
- related:
  - verb: has
    entity: regular-user
- related:
  - verb: has
    entity: view-only-user
references:
- kind: code
  role: implementation
  target: server.js
---

# A user account is changed by an Admin, or by its own person for their theme and language

Every signed-in person keeps their own theme and interface language; everything else about an account is the Admin's.
