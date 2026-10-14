---
domain: files
relations:
- entity: file
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server.js
---

# Folder

A folder inside the G-code folder.

## Information kept

- **Name** — unique within its parent folder
