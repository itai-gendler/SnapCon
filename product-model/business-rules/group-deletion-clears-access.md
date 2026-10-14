---
appliesTo:
- type: capability
  id: delete-group
  contexts:
  - place: web::settings
references:
- kind: code
  role: implementation
  target: groupAccess.js#removeGroupReferences
---

# Deleting a group takes it off every printer and person

Printers and people left with no group fall back to Everyone.
