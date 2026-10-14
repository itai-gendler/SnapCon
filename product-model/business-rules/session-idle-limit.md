---
appliesTo:
- type: capability
  id: sign-in
- type: capability
  id: sign-out
references:
- kind: code
  role: implementation
  target: auth.js
---

# A session ends after 18 hours without use

Every request while signed in extends the session.
