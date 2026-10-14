---
actors:
- admin
- regular-user
- view-only-user
access: authenticated
entryPoints:
- web: /
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: auth.js#requireAuth
- kind: code
  role: implementation
  target: auth.js#requireRegular
---

# Fleet

Everything a signed-in person works with day to day: the fleet dashboard and its views, the file list and the Send dialogs, the Print Farm view of the queues, printer health and maintenance. View Only users watch; Regular users and Admins also operate printers and jobs.
