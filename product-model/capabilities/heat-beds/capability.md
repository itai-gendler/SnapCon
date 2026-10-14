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
  target: public/app.js
---

# Heat beds

Set the bed temperature of one printer with Preheat, or of many at once, optionally staggered so a shared circuit is not overloaded.
