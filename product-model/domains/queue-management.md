---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Queue Management

Settings → Queue Management: turning queues on and the Printer Pools.

## Boundary

Queue Management owns the feature switch and Printer Pools. It does not own each printer's queue or its jobs.
