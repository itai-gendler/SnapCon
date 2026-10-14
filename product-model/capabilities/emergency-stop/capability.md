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

# Emergency stop

Halt a printer at once with E-Stop.
