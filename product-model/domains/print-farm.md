---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Print Farm

The Print Farm view of Queue Management: every printer's queue, its jobs and the actions that move it on.

## Boundary

Print Farm owns printer queues and queued jobs once they exist. It does not own creating Printer Pools, assigning printers to them or turning Queue Management on.
