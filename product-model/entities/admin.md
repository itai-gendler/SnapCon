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
  target: auth.js#requireAdmin
- kind: doc
  role: intent
  target: README.md
---

# Admin

A person with full access: every printer whatever its groups, every printer and job action, and all of Settings. While User Access Management is off, everyone who opens SnapCon acts as an Admin.
