---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#computeAutoBalanceMoves
- kind: code
  role: implementation
  target: server.js
---

# Balance pool queues

In pools with Auto-balance on, SnapCon moves the oldest waiting job from the busiest printer to an idle printer of the same connector whose queue is empty.
