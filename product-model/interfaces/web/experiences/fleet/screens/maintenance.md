---
entities:
- entity: printer
  shows:
  - Name
  - Total print hours
  - Warranty
  - Next maintenance
- entity: maintenance-entry
  shows:
  - Date
  - Component
  - Part
  - Notes
  - Cost
  - Print hours
  - Reminder
  - Next due
  collects:
  - Date
  - Component
  - Part
  - Notes
  - Cost
  - Reminder
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Maintenance

One printer's maintenance: print hours, warranty, last and next service, the service history, logging a new entry and taking the printer offline or bringing it back.
