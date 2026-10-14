---
appliesTo:
- type: entity
  id: printer
  facts:
  - Warranty
  - Purchase date
references:
- kind: code
  role: implementation
  target: server.js#computeWarranty
---

# A printer's warranty lasts twelve months from its purchase date

It shows as expiring in the last 30 days and expired after; without a purchase date it is unknown.
