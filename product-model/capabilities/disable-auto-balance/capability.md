---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
---

# Disable auto-balance

Stop moving jobs between a Printer Pool's printers.
