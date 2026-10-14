---
appliesTo:
- type: capability
  id: heat-beds
  contexts:
  - place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: public/app.js
---

# A bed target is between 0 °C and the printer's maximum, never above 120 °C

0 turns the bed heater off.
