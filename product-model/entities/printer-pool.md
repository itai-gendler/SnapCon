---
domain: queue-management
relations:
- entity: printer
  verb: contains
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server.js#sanitizePrinterPool
---

# Printer pool

A set of printers that share Send to Queue and Auto-Balance and the way the bed is cleared between queued prints.

## Information kept

- **Name** — the pool's name
- **Bed clear** — how the bed is cleared between queued prints: Manual
- **Auto-balance** — whether an idle printer with an empty queue takes work from a busier printer of the pool
- **Built-in** — whether it is the protected Unassigned pool
