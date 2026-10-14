---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#resolveAttention
- kind: code
  role: implementation
  target: server.js
---

# Acknowledge queue recovery

After a restart found a printer printing something the queue did not send, accept what the printer is doing and let the queue go on.
