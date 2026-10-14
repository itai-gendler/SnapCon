---
entities:
- entity: printer
  shows:
  - Name
  - Attention reasons
  - Temperatures
  - Total print hours
  - Warranty
  - Next maintenance
- entity: maintenance-entry
  shows:
  - Date
  - Component
entryPoints:
- web: /health/<printer id>
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Printer health

One printer's diagnostics as the printer reports them: heaters, fans, controller, storage and faults, with what needs attention, its service history, warranty and the offline switch.
