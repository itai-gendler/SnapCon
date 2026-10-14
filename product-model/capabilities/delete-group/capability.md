---
domain: users
availability:
- place: web::settings
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: groupAccess.js#removeGroupReferences
---

# Delete group

Delete a group other than Everyone after confirming; printers and people left without any group fall back to Everyone.
