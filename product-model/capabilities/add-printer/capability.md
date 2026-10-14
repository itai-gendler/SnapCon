---
domain: printers
availability:
- place: web::settings
references:
- kind: code
  role: implementation
  target: server.js#buildPrinterRecord
- kind: code
  role: implementation
  target: connectors/address.js
---

# Add printer

Add a printer by hand, or from network discovery, with its identity, connection, hardware and print behavior.
