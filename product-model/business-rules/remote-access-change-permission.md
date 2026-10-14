---
appliesTo:
- type: entity
  id: remote-access
  effect: changes
permits:
- actors:
  - admin
- unattended: true
references:
- kind: code
  role: implementation
  target: server.js
---

# Only an Admin turns Remote Access on, off or removes it

SnapCon itself completes the connection after verification.
