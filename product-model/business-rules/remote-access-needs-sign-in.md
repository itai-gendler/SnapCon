---
appliesTo:
- type: capability
  id: enable-remote-access
- type: capability
  id: change-user-access-settings
- type: capability
  id: delete-user
references:
- kind: code
  role: implementation
  target: remote-access/RemoteAccessService.js#validateRemoteAccessSecurity
- kind: code
  role: implementation
  target: server.js
---

# Remote Access runs only while sign-in is required

Remote Access is enabled only with User Access Management on and an Admin account; while it is on, User Access Management cannot be turned off and the only remaining account cannot be deleted.
