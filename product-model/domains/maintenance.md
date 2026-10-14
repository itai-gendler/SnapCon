---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Maintenance

Each printer's service records and its offline switch.

## Boundary

Maintenance owns maintenance entries and taking printers offline. It does not own the health diagnostics the printer reports or the purchase date set in printer settings.
