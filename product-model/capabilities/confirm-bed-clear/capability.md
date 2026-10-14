---
domain: print-farm
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js#confirmManualBedClear
---

# Confirm bed clear

Confirm that the bed of a printer whose queued print finished has been cleared, so its next job can dispatch.
