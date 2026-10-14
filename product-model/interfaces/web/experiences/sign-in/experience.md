---
actors:
- admin
- regular-user
- view-only-user
access: public
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Sign-in

What a person sees before signing in while User Access Management is on: the login form, by password or by a one-time code.
