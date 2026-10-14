---
references:
- kind: code
  role: implementation
  target: server.js
---

# Printer file

A file stored on a printer: sent there by SnapCon or the slicer hook, or already in the printer's own storage.

## Information kept

- **Name** — its name on the printer
- **Size** — in bytes
- **Colors** — the filament colors it needs
- **Estimated time** — the print time the printer reports

## States

### Sending

SnapCon is uploading it to the printer.

### Waiting for printer

SnapCon holds it until the printer is idle, then sends it.

### Ready to print

Staged on the printer by SnapCon, one click from printing.

### Stored

In the printer's storage.

### Upload failed

Sending it stopped; the printer card says why.
