---
actors:
- admin
access: restricted
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: auth.js#requireAdmin
- kind: code
  role: implementation
  target: public/index.html
---

# Settings

The Settings area only Admins open: General, View, Notifications, Printers, Users, Remote Access, Logs and Queue Management.
