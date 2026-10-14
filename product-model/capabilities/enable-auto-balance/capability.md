---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
---

# Enable auto-balance

Let a Printer Pool's idle printers with empty queues take jobs from the busiest printer of the same kind.
