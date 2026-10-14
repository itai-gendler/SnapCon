---
availability:
- place: web::sign-in
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: auth.js#verifyOtpCode
- kind: code
  role: implementation
  target: auth.js#createSession
---

# Sign in

Sign in while User Access Management is on, with a login name and password, or with a one-time code SnapCon sends by email, ntfy.sh or Telegram.
