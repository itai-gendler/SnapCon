---
domain: fleet
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
- kind: code
  role: implementation
  target: public/app.js
---

# Monitor fleet

Watch every printer one may see on the fleet dashboard — status, current print, temperatures, toolhead filament, staged file, queue state and what needs attention — in the Full, Compact, Camera or List view, searched, filtered and sorted.
