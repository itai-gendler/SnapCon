---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
---

# Remove queued job

Take a waiting job out of a Printer queue.
