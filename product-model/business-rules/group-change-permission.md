---
appliesTo:
- type: entity
  id: group
  effect: changes
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

# Only an Admin renames a group, never Everyone

The built-in Everyone group keeps its name.
