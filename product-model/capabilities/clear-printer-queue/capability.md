---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: queue/QueueEngine.js#clearQueue
---

# Clear printer queue

Cancel the print a queue is running and remove every waiting job of that printer in one step, after confirming.
