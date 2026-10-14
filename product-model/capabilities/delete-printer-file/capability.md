---
domain: files
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#printerFileDeleteRefusal
---

# Delete printer file

Delete a file from a printer's own storage when nothing in SnapCon still needs it.
