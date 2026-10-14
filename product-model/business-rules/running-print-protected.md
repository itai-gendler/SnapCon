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
  target: server.js#activeJobConflict
- kind: code
  role: implementation
  target: server.js#assertNotActiveJobFile
---

# The file a printer is printing is never overwritten or restarted

Sending a file with the name of the one printing or paused is refused, and so is starting the very file already printing; SnapCon checks the printer live just before every send, including queued and held ones.
