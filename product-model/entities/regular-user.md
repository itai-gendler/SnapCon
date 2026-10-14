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
  target: auth.js#requireRegular
- kind: doc
  role: intent
  target: README.md
---

# Regular user

A person who operates printers and manages jobs on the printers their groups may use, without access to Settings.
