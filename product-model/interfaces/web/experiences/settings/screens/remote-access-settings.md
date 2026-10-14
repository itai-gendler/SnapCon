---
entities:
- entity: remote-access
  shows:
  - Public address
  - Verification link
  - Last connected
- entity: user-account
  shows:
  - Login name
  - One-time code sign-in
- entity: settings
  shows:
  - User access management
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: remote-access/RemoteAccessService.js
---

# Remote Access settings

Whether Remote Access is on, its public address and connection, the one-time verification step, who can sign in through it, and its diagnostics.
