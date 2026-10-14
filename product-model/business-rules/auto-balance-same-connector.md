---
appliesTo:
- type: capability
  id: balance-pool-queues
  contexts:
  - place: web::fleet
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#computeAutoBalanceMoves
---

# Auto-balance moves a job only between printers of the same connector in the same pool

The oldest waiting job of the printer with the longest queue moves to a printer that is idle with an empty queue, so a job's head mapping always fits where it goes.
