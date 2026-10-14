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

# View activity log

Read the activity log of sign-ins, job actions and administrative changes, filtered by date range, category or text.
