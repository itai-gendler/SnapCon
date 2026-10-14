---
domain: print-farm
relations:
- entity: queued-job
  verb: holds
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js
- kind: code
  role: implementation
  target: queue/QueueStore.js
---

# Printer queue

The ordered list of jobs one printer in a Printer Pool prints in turn, and where that printer stands between jobs.

## Information kept

- **Paused** — dispatch of the next job is held; the current print continues
- **Stopped** — dispatch is stopped until resumed; the current print continues
- **Attention reason** — why the queue waits for a person: print failed, dispatch failed, file missing, file changed or interrupted by a restart
- **Current job** — the job printing or last handled
- **Jobs waiting** — how many jobs wait
- **Recent history** — the last 20 finished, failed, skipped, cancelled or removed jobs

## States

### Idle

Nothing is printing; the next job dispatches when the printer is free.

### Dispatching

SnapCon is checking, sending and starting the next job.

### Printing

A queued job is printing.

### Awaiting bed clear

The last queued print finished and a person must clear the bed.

### Needs attention

Something went wrong and a person must decide how to go on.
