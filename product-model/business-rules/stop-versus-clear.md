---
appliesTo:
- type: capability
  id: stop-printer-queue
- type: capability
  id: pause-printer-queue
- type: capability
  id: clear-printer-queue
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#clearQueue
---

# Stopping a queue keeps the current print and the waiting jobs; clearing it cancels and removes them

Stop and Pause only hold dispatch; Clear Queue cancels the running print and removes every waiting job, and is confirmed first because it cannot be undone.
