---
appliesTo:
- type: entity
  id: printer
  effect: changes
  facts:
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
  - Position
  - Groups with access
  - Printer pool
permits:
- actors:
  - admin
references:
- kind: code
  role: implementation
  target: auth.js#requireAdmin
- kind: code
  role: implementation
  target: server.js
---

# Only an Admin changes a printer's configuration, tags, order, groups or pool

Identity, connection, credentials, hardware, print behavior, tags, position, the groups that may use it and its Printer Pool are Admin settings, even where they are edited from the fleet dashboard.
