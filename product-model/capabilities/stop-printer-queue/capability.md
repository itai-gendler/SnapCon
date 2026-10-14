---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#stopQueue
---

# Stop printer queue

Stop a printer's queue after confirming, so nothing more dispatches until it is resumed; the current print and the waiting jobs stay.
