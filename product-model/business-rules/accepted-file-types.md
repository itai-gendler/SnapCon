---
appliesTo:
- type: capability
  id: print-file
- type: capability
  id: upload-file-to-printer
- type: capability
  id: send-file-from-slicer
references:
- kind: code
  role: implementation
  target: server.js#fileTypeRefusal
---

# A printer receives only the file types it can print

A file of another type is refused before anything is sent: plain printers take .gcode, .gco, .g, .gx and .3mf, while a Bambu Lab printer takes only what its firmware runs.
