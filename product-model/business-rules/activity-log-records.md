---
appliesTo:
- type: entity
  id: activity-log-entry
- type: entity
  id: printer
  effect: changes
- type: entity
  id: queued-job
  effect: creates
- type: entity
  id: queued-job
  effect: removes
- type: entity
  id: user-account
  effect: creates
- type: entity
  id: user-account
  effect: changes
- type: entity
  id: user-account
  effect: removes
- type: entity
  id: group
  effect: creates
- type: entity
  id: group
  effect: removes
- type: entity
  id: printer-pool
  effect: creates
- type: entity
  id: settings
  effect: changes
- type: entity
  id: remote-access
  effect: changes
references:
- kind: code
  role: implementation
  target: audit/AuditLog.js
- kind: code
  role: implementation
  target: server.js
---

# Sign-ins, job actions and administrative changes are recorded in the activity log

Every print started, uploaded, controlled, queued or finished, every sign-in and sign-out, and every change to settings, printers, users, groups, pools and Remote Access is recorded with who did it, the printer and the time.
