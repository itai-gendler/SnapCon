---
entities:
- entity: settings
  shows:
  - Queue management
- entity: printer-pool
  shows:
  - Name
  - Built-in
  - Bed clear
  collects:
  - Name
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Queue Management settings

Whether Queue Management is on and the Printer Pools printers can belong to, including the built-in Unassigned pool.
