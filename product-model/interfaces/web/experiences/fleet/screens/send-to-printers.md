---
entities:
- entity: file
  shows:
  - Name
  - Colors
  - Sliced for
  - Estimated time
- entity: printer
  shows:
  - Name
  - Online
  - Print defaults
- entity: toolhead
  shows:
  - Number
  - Filament color
  - Material
- entity: printer-file
  shows:
  - Name
  - Size
- entity: settings
  shows:
  - Head mapping
  - Auto-match colors
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Send to printers

Sending one file to one or several printers: which printers, which toolhead prints each color of the file, the print options, and Upload or Upload & Print, with progress per printer.
