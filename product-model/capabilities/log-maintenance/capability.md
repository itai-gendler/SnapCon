---
domain: maintenance
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#computeNextScheduled
- kind: code
  role: implementation
  target: server.js#computeNextMaintenance
---

# Log maintenance

Record a service of a printer's component, with an optional part, notes, cost and a reminder that schedules the next service.
