---
kind: system
acts: external
references:
- kind: code
  role: implementation
  target: server.js
- kind: doc
  role: intent
  target: README.md
---

# Slicer

A slicer on the SnapCon machine whose post-processing step runs the slicer hook to hand a sliced file to a printer by its name in SnapCon.
