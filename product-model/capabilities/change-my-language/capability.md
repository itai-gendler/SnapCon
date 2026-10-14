---
availability:
- place: web::fleet
- place: web::settings
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: public/app.js#saveUserLocalePreference
---

# Change my language

Choose one's own interface language, or follow the system default, from the top bar or, for an Admin, in Settings → View.
