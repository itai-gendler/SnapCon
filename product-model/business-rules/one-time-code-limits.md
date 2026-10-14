---
appliesTo:
- type: capability
  id: sign-in
  contexts:
  - place: web::sign-in
references:
- kind: code
  role: implementation
  target: auth.js#verifyOtpCode
---

# A one-time code is eight characters, valid ten minutes, for five attempts and one use

Codes avoid look-alike characters; an expired or exhausted code is discarded and a new one must be requested.
