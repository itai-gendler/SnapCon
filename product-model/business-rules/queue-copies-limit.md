---
appliesTo:
- type: capability
  id: send-to-queue
  contexts:
  - place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
---

# A file is queued 1 to 50 times per request

Send to Queue takes between one and fifty copies of each file.
