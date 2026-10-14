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
  target: groupAccess.js#printerVisibleTo
---

# Grant printer access

Let a group see and use a printer.
