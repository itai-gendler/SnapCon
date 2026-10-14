---
appliesTo:
- type: capability
  id: watch-prints
- type: entity
  id: settings
  facts:
  - Filament cost
  - Electricity rate
references:
- kind: code
  role: implementation
  target: server.js#notifyTick
---

# A print's cost is estimated from filament used and print time at the rates set when it finishes

Filament weight assumes 1.75 mm filament at about 1.24 g/cm³; energy uses the electricity rate. The estimate recorded is never recalculated later.
