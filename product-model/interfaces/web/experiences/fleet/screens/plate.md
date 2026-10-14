---
entities:
- entity: printer
  shows:
  - Name
  - Plate objects
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Exclude objects

The objects of a printer's current print, on a map of the bed and as a list, showing which one is printing and which are already excluded.
