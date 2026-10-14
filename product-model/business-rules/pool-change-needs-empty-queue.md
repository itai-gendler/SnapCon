---
appliesTo:
- type: capability
  id: change-printer-pool
  contexts:
  - place: web::settings
references:
- kind: code
  role: implementation
  target: server.js
---

# A printer changes pool only while its queue is idle and empty

A printer that prints only some file types cannot join a pool, because a pool sends the same file to every printer in it; leaving a pool is always allowed.
