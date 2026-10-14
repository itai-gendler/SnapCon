---
actors:
- admin
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: remote-access/RemoteAccessService.js
---

# Open SnapCon to remote access

## Goal

An Admin who tries to enable Remote Access without sign-in is taken to Users to require sign-in, then enables Remote Access.

## Success criterion

Remote Access is connected and sign-in is required.
