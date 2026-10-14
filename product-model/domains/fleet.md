---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Fleet

The fleet dashboard: watching every printer and acting on prints, beds, filament and tags from its cards and toolbars.

## Boundary

Fleet owns watching printers and controlling their current print, bed heat, toolhead filament and tags. It does not own sending files, the queues, maintenance records or printer configuration.
