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

# Use current file

Accept that a queued job's file changed since it was queued and print the file as it is now.
