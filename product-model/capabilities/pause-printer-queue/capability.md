---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#pauseQueue
---

# Pause printer queue

Hold a printer's queue, or every queue of a pool with Pause All Queues, so no further job dispatches; the current print continues.
