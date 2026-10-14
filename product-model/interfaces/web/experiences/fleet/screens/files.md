---
entities:
- entity: folder
  shows:
  - Name
  collects:
  - Name
- entity: file
  shows:
  - Name
  - Size
  - Modified
  - Colors
  - Estimated time
  - Filament weight
  - Estimated cost
  - Thumbnail
  - Full Spectrum
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Files

The file list beside the fleet: folders and sliced files of the G-code folder with their colors, print time, weight, cost estimate and thumbnail, a search across every subfolder, and multi-select for moving files or sending them to a queue.
