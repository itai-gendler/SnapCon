---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#attemptQueueDispatch
- kind: code
  role: implementation
  target: queue/QueueEngine.js#claimTransition
- kind: code
  role: implementation
  target: queue/QueueEngine.js#reconcileOnStartup
---

# Dispatch queued job

SnapCon's own sweep sends and starts the next job of every idle queue whose printer is free, after checking the file is still the one that was queued.
