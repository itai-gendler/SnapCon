---
domain: logs
references:
- kind: code
  role: implementation
  target: audit/AuditLog.js
---

# Activity log entry

One recorded sign-in, job action or administrative change, kept apart from the printers and settings so it survives their renaming or removal.

## Information kept

- **Time** — when it happened
- **Category** — Jobs, Admin or Sign-ins
- **Event** — what happened
- **User** — who did it; empty when it happened on the printer itself or without sign-in
- **Printer** — the printer concerned
- **Detail** — the file, the change made, or a finished print's time, filament and cost estimate
