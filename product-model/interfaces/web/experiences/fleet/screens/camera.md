---
entities:
- entity: printer
  shows:
  - Name
  - Camera
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Camera snapshot

The latest camera image of one printer, refreshed on request.
