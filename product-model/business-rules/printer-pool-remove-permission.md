---
appliesTo:
- type: entity
  id: printer-pool
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

# Only an Admin deletes a Printer pool, never Unassigned

The built-in Unassigned pool is never deleted.
