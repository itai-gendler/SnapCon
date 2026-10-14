---
appliesTo:
- type: capability
  id: log-maintenance
- type: entity
  id: maintenance-entry
  facts:
  - Next due
references:
- kind: code
  role: implementation
  target: server.js#computeNextScheduled
- kind: code
  role: implementation
  target: server.js#computeMaintenanceAttention
---

# A reminder sets the next due date; maintenance is due soon within 14 days and overdue after it

Weekly adds seven days, monthly one month and quarterly three months to the service date. For each component only its latest entry counts, and the soonest of them is the printer's next maintenance.
