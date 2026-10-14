---
domain: maintenance
references:
- kind: code
  role: implementation
  target: server.js#computeNextScheduled
---

# Maintenance entry

One service record of a printer, kept by the printer's identity so it survives renaming and removal.

## Information kept

- **Date** — when the service was done
- **Component** — the part or operation serviced
- **Part** — the replacement part, optional
- **Notes** — optional
- **Cost** — optional
- **Print hours** — the printer's total print hours when it was logged
- **Reminder** — none, weekly, monthly or quarterly
- **Next due** — the date the reminder falls due
