---
type: cli
actors:
- slicer
entryPoints:
- cli: snapcon --load <file> --printer <name in SnapCon> [--outputname <display name>]
references:
- kind: code
  role: implementation
  target: server.js
- kind: doc
  role: intent
  target: README.md
---

# Slicer hook

The command a slicer's post-processing step runs on the SnapCon machine to hand a freshly sliced file to a named printer without opening the browser.
