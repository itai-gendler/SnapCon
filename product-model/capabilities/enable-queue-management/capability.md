---
domain: queue-management
availability:
- place: web::settings
references:
- kind: code
  role: implementation
  target: server.js
---

# Enable queue management

Turn on Queue Management; every printer without a pool joins the built-in Unassigned pool.
