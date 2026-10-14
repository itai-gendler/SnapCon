---
entities:
- entity: file
  shows:
  - Name
- entity: printer-pool
  shows:
  - Name
- entity: printer
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Send to Queue

Sending the selected files to a Printer Pool: copies of each file, Print on All or Distribute, and a preview of which printer gets which job.
