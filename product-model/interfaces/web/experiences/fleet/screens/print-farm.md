---
entities:
- entity: printer-pool
  shows:
  - Name
  - Auto-balance
- entity: printer
  shows:
  - Name
  - Current print
- entity: printer-queue
  shows:
  - Paused
  - Stopped
  - Attention reason
  - Current job
  - Jobs waiting
  - Recent history
- entity: queued-job
  shows:
  - File
  - Queued by
  - Queued at
  - Finished at
- entity: file
  shows:
  - Name
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Print Farm

The Queue Management dashboard: fleet utilization, each Printer Pool with its printers' queue state, the current and waiting jobs of every printer, and the actions that move a queue on.
