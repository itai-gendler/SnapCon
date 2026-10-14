---
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#uploadDisposition
- kind: code
  role: implementation
  target: server.js#decideUpload
- kind: code
  role: implementation
  target: server.js#uploadNotifiedFile
---

# Upload file to printer

Send a file to one or several printers without starting it, so it is staged on each printer ready to print; a busy printer receives it when it is free.
