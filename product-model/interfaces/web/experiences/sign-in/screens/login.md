---
entities:
- entity: user-account
  collects:
  - Login name
  - Password
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Login

The sign-in form shown while User Access Management is on and nobody is signed in: a login name with a password, or a one-time code sent to the configured service.
