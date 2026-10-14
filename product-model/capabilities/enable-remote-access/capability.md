---
domain: remote-access
availability:
- place: web::settings
references:
- kind: code
  role: implementation
  target: remote-access/RemoteAccessService.js
- kind: code
  role: implementation
  target: server.js
- kind: doc
  role: intent
  target: README.md
---

# Enable remote access

Give SnapCon a public HTTPS address through a managed tunnel, after a one-time verification of the installation.
