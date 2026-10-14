---
appliesTo:
- type: entity
  id: activity-log-entry
- type: entity
  id: settings
  facts:
  - Log retention
references:
- kind: code
  role: implementation
  target: audit/AuditLog.js
- kind: code
  role: implementation
  target: server.js
---

# The activity log keeps entries for the retention period, 90 days unless set otherwise

Older entries are pruned daily.
