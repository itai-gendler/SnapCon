---
availability:
- place: slicer-hook
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: notifyToken.js
- kind: doc
  role: intent
  target: README.md
---

# Send file from slicer

A slicer's post-processing step hands a sliced file to a printer by its name in SnapCon; SnapCon uploads it and stages it ready to print, never starting it.
