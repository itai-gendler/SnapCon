---
appliesTo:
- type: entity
  id: file
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

# Files are uploaded to the G-code folder by an Admin or a Regular user

Uploading from one's computer is not limited by printer groups.
