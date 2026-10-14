---
relations:
- entity: admin
  verb: includes
  cardinality: many-to-many
- entity: regular-user
  verb: includes
  cardinality: many-to-many
- entity: view-only-user
  verb: includes
  cardinality: many-to-many
domain: users
references:
- kind: code
  role: implementation
  target: groupAccess.js#printerVisibleTo
- kind: code
  role: implementation
  target: server.js
---

# Group

A named set of people that decides which printers they see and use. The built-in Everyone group holds every person and printer that has no group of its own.

## Information kept

- **Name** — the group's name
- **Built-in** — whether it is the protected Everyone group
