---
kind: primary
routes:
  cli: Command line
steps:
- text: The Slicer runs the hook with the sliced output, the printer's name in SnapCon and an optional display name
  kind: actor
  actor: slicer
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    cli:
      place: slicer-hook
- text: The name matches a printer, ignoring case and with underscores for spaces, and the printer accepts that kind of output
  kind: condition
  actor: slicer
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Connector
  contexts:
    cli:
      place: slicer-hook
- text: The Product uploads it under the display name and stages it as a Printer file ready to print
  kind: product
  actor: slicer
  entities:
  - entity: printer-file
    effect: creates
    to: Ready to print
    facts:
    - Name
    - Size
  - entity: printer
    effect: reads
    facts: []
  contexts:
    cli:
      place: slicer-hook
---

# Hand a sliced file to a printer

## Trigger

A person clicks upload in the slicer after slicing.

## Outcome

The printer card shows the file ready to print; the hook reports where it went.
