---
appliesTo:
- type: capability
  id: confirm-bed-clear
- type: capability
  id: retry-queued-job
- type: capability
  id: skip-queued-job
- type: capability
  id: watch-prints
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js
---

# After every queued print a person confirms the bed is clear before the next job

Every pool clears the bed manually. A job that never started printing — a failed dispatch or a missing or changed file — needs no bed clear when it is retried or skipped.
