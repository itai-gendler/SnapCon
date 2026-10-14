---
appliesTo:
- type: capability
  id: delete-printer-file
  contexts:
  - place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#printerFileDeleteRefusal
---

# A file on a printer is not deleted while SnapCon still needs it

Deletion is refused while the printer starts a print, prints or receives that file, while the file waits in the printer's queue, and when the printer cannot be asked.
