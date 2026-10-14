---
type: web
actors:
- admin
- regular-user
- view-only-user
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: public/index.html
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: auth.js#makeAuthMiddleware
---

# SnapCon web app

The browser application SnapCon serves on its own port on the local network, and through a public address while Remote Access is on: the fleet dashboard with its file list, Print Farm view, health and maintenance pages, and the Settings area for Admins.
