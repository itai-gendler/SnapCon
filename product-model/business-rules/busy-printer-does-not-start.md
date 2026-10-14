---
appliesTo:
- type: capability
  id: print-file
- type: capability
  id: upload-file-to-printer
- type: capability
  id: dispatch-queued-job
- type: capability
  id: send-file-from-slicer
references:
- kind: code
  role: implementation
  target: server.js#uploadDisposition
- kind: code
  role: implementation
  target: server.js#isPrinterIdle
---

# A print is started only on a free printer

Upload & Print to a printing printer is refused; uploading to it is allowed. Queue dispatch, held uploads and the slicer hook wait until the printer is idle, complete or cancelled and not starting another print.
