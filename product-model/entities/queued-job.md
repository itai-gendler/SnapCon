---
domain: print-farm
references:
- kind: code
  role: implementation
  target: queue/QueueEngine.js
- kind: code
  role: implementation
  target: server.js
---

# Queued job

One print of one file waiting in, or dispatched from, a Printer queue.

## Information kept

- **File** — the file's name and folder
- **Content fingerprint** — the size and hash of the file when it was queued
- **Head mapping** — which toolhead prints each color
- **Print options** — auto-leveling, flow calibration and time-lapse for this job
- **Queued by** — who queued it
- **Queued at** — when it was queued
- **Finished at** — when it completed, failed or was skipped, cancelled or removed
- **Retry of** — the job it retries

## States

### Queued

Waiting its turn.

### Dispatching

Being checked, sent and started.

### Printing

Printing on its printer.

### Completed

The print finished.

### Failed

Its dispatch or print failed.

### Skipped

A person skipped it.

### Cancelled

Cancelled while printing when the queue was cleared.
