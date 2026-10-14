---
domain: files
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: parser.js#parseGcodeMap
---

# File

A sliced file (.gcode, .gco, .g, .gx or .3mf) in the G-code folder SnapCon watches.

## Information kept

- **Name** — its file name
- **Size** — in bytes
- **Modified** — when it last changed
- **Colors** — the filament colors the print needs, read from the file
- **Estimated time** — the slicer's print time estimate
- **Filament weight** — the slicer's filament estimate
- **Estimated cost** — filament and energy cost from the cost rates
- **Thumbnail** — the preview image the slicer embedded
- **Sliced for** — the printer model and nozzle the file was sliced for, where the file says
- **Full Spectrum** — whether it is a Full Spectrum file, and which fork produced it
