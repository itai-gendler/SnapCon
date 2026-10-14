---
appliesTo:
- type: capability
  id: change-user-access-settings
- type: capability
  id: edit-user
- type: capability
  id: delete-user
references:
- kind: code
  role: implementation
  target: server.js
---

# Sign-in is required only while an Admin account exists

User Access Management cannot be turned on before an Admin account exists, and the last Admin can be neither demoted nor deleted, so nobody is locked out.
