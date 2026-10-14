---
domain: files
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js
- kind: code
  role: implementation
  target: parser.js#parseGcodeMap
---

# Browse files

Browse the G-code folder's folders and sliced files, search every subfolder, and see each file's colors, estimates and thumbnail.
