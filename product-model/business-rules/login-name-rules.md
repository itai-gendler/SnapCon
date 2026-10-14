---
appliesTo:
- type: entity
  id: user-account
  facts:
  - Login name
- type: capability
  id: create-user
- type: capability
  id: edit-user
references:
- kind: code
  role: implementation
  target: server.js
---

# Login names are 2 to 32 characters and unique ignoring case

Letters, digits, underscore, dot and hyphen only; two accounts never share a login name in any letter case.
