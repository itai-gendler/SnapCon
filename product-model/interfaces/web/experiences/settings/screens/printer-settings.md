---
entities:
- entity: printer
  shows:
  - Name
  - Location
  - Brand
  - Connector
  - Address
  - Serial number
  - Purchase date
  - Power draw
  - Print defaults
  - Force default behavior
  - Tags
  - Groups with access
  - Printer pool
  - Position
  collects:
  - Name
  - Location
  - Brand
  - Connector
  - Address
  - Credentials
  - Serial number
  - Purchase date
  - Power draw
  - Print defaults
  - Force default behavior
  - Tags
  - Groups with access
  - Printer pool
- entity: group
  shows:
  - Name
- entity: printer-pool
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js#buildPrinterRecord
---

# Printer settings

Every printer SnapCon manages, each with its identity, connection, hardware, print behavior, tags, the groups that may use it and its Printer Pool, in the fleet's order.
