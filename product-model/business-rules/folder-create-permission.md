---
appliesTo:
- type: entity
  id: folder
  effect: creates
permits:
- actors:
  - admin
- actors:
  - regular-user
references:
- kind: code
  role: implementation
  target: auth.js#requireRegular
---

# Folders are created by an Admin or a Regular user

Creating folders is not limited by printer groups.
