---
appliesTo:
- type: entity
  id: activity-log-entry
  effect: reads
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
---

# Only an Admin reads the activity log

The log names users, printers and files.
