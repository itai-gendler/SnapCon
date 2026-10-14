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

# Retry queued job

Put a fresh copy of a failed job at the front of the queue.
