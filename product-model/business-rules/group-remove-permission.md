---
appliesTo:
- type: entity
  id: group
  effect: removes
permits:
- actors:
  - admin
  when:
  - fact: Built-in
    is: 'No'
references:
- kind: code
  role: implementation
  target: server.js
---

# Only an Admin deletes a group, never Everyone

The built-in Everyone group is never deleted.
