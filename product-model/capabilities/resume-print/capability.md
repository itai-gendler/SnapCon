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

# Resume print

Resume a paused print, from its card, for several selected printers, or from the Print Farm view when a queued print paused on failure.
