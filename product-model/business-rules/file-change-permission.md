---
appliesTo:
- type: entity
  id: file
  effect: changes
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

# Files in the G-code folder are moved by an Admin or a Regular user

Moving files is not limited by printer groups.
