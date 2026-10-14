---
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: server.js#runPrintFileJob
---

# Print file

Start a print: send a file from the file list to one or several printers with Upload & Print, print the file staged on a printer, reprint its last file, or pick a file already stored on it.
