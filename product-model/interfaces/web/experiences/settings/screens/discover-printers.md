---
entities:
- entity: printer
  shows:
  - Name
  - Address
  - Brand
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Discover printers

A scan of the local network, or of one subnet, for supported printers, each found printer with its address and an Add button, already configured ones marked Added.
