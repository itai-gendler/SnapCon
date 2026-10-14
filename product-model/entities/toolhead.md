---
domain: fleet
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Toolhead

One head or filament slot of a printer — a U1 toolhead, an AMS tray or an IFS slot — with the filament the printer reports in it.

## Information kept

- **Number** — 1 to 4, or T0 to T3 with T-notation
- **Filament color** — the color stored on the printer for the loaded filament
- **Material** — the filament material stored on the printer

## States

### Loaded

Filament is in the toolhead.

### Empty

No filament is loaded; it shows as an empty slot.
