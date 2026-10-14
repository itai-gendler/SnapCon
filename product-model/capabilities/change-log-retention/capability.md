---
domain: logs
availability:
- place: web::settings
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: audit/AuditLog.js
---

# Change log retention

Set how many days the activity log keeps entries.
