---
appliesTo:
- type: entity
  id: group
- type: entity
  id: printer
  facts:
  - Groups with access
- type: entity
  id: user-account
  facts:
  - Groups
references:
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
- kind: code
  role: implementation
  target: server.js
---

# A printer or person with no group belongs to Everyone

Everyone always exists. A printer shared with no group is shared with Everyone, and a person in no group is in Everyone, so both meet there; once either has a group of its own, Everyone no longer applies to it. Admins see every printer whatever the groups.
