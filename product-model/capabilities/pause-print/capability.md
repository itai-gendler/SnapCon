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
  target: connectors/http-utils.js
---

# Pause print

Pause a printer's print, one printer from its card or several selected in the Camera or List view.
