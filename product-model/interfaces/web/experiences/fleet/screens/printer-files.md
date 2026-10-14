---
entities:
- entity: printer
  shows:
  - Name
- entity: printer-file
  shows:
  - Name
  - Size
  - Colors
  - Estimated time
- entity: toolhead
  shows:
  - Number
  - Filament color
  - Material
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Print from printer

The files already stored on one printer, with their colors and print time, to print one or delete it.
