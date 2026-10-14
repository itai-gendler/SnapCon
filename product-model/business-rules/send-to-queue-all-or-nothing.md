---
appliesTo:
- type: capability
  id: send-to-queue
  contexts:
  - place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
---

# Send to Queue queues every file or none

Every file is checked before anything is queued, so one bad file never leaves a partial batch.
