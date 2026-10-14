---
appliesTo:
- type: capability
  id: resume-print
  contexts:
  - place: web::fleet::print-farm
- type: capability
  id: retry-queued-job
- type: capability
  id: skip-queued-job
- type: capability
  id: use-current-file
- type: capability
  id: acknowledge-queue-recovery
- type: capability
  id: stop-printer-queue
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js
---

# Each reason a queue needs attention offers its own ways on

A failed print offers Resume, Retry job, Skip job or Stop Queue; a failed dispatch Retry job, Skip job or Stop Queue; a missing file Skip job or Stop Queue; a changed file Use current file, Skip job or Stop Queue; an unexpected print found after a restart Acknowledge & resume or Stop Queue; an interrupted dispatch Retry job, Skip job or Stop Queue; a print whose end went unseen Resume, Retry job, Skip job or Stop Queue.
