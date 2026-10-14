---
entities:
- entity: activity-log-entry
  shows:
  - Time
  - Category
  - Event
  - User
  - Printer
  - Detail
- entity: settings
  shows:
  - Log retention
  collects:
  - Log retention
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: audit/AuditLog.js
---

# Logs

The activity log, filtered by date range, category or text, and how many days it is kept.
