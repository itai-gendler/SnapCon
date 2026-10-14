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
  target: queue/QueueEngine.js#resumeFromStop
---

# Resume printer queue

Let a paused or stopped queue dispatch again; a stopped queue first checks the printer live.
