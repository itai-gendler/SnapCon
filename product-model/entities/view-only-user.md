---
kind: person
acts: external
relations:
- entity: user-account
  verb: has
  cardinality: one-to-one
references:
- kind: code
  role: implementation
  target: auth.js#requireAuth
- kind: doc
  role: intent
  target: README.md
---

# View-only user

A person who monitors the printers their groups may use and performs no printer actions.
