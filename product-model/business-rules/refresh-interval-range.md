---
appliesTo:
- type: capability
  id: change-general-settings
- type: capability
  id: monitor-fleet
references:
- kind: code
  role: implementation
  target: server.js
---

# Printers are checked every 1 to 60 seconds

An offline printer is retried every ten seconds rather than on every check.
