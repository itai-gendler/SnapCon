---
appliesTo:
- type: entity
  id: user-account
  facts:
  - Password
  - One-time code sign-in
- type: capability
  id: sign-in
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: auth.js
---

# Every account signs in with a password of at least 8 characters or with one-time codes, never both

An account with OTP login has no usable password; switching back to password sign-in needs a password on file.
