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

# Cancel print

Cancel a printer's print after confirming, from its card, for several selected printers, or from the Print Farm view.
