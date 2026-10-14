---
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Notifications

Settings → Notifications: which print events reach which services.

## Boundary

Notifications owns notification settings and test messages. It does not own one-time code delivery for sign-in, which belongs to Users.
