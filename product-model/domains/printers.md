---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Printers

Settings → Printers: adding, configuring, ordering and removing printers, their group access and their Printer Pool.

## Boundary

Printers owns printer configuration. It does not own the groups or pools a printer is assigned to, or anything about its prints.
