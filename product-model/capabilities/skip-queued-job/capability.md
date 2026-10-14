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

# Skip queued job

Give up on the job a queue is stuck on and go on with the next one.
