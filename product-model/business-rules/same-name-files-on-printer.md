---
appliesTo:
- type: capability
  id: print-file
- type: capability
  id: upload-file-to-printer
- type: capability
  id: dispatch-queued-job
references:
- kind: code
  role: implementation
  target: server.js#decideUpload
---

# A file the printer already has is not sent again, and a different file of that name is replaced only when allowed

With Skip identical uploads on, a byte-identical copy is used without sending. With Overwrite different files off, a different file of the same name is refused; a copy SnapCon cannot check is always sent.
