---
kind: primary
routes:
  cli: Command line
steps:
- text: The Slicer runs the hook for a printer that is printing
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
- text: The Product holds the sliced output until the printer is idle
  kind: product
  actor: slicer
  entities:
  - entity: printer-file
    effect: creates
    to: Waiting for printer
    facts:
    - Name
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    cli:
      place: slicer-hook
- text: Once the printer is idle the Product uploads it and stages it ready to print
  kind: product
  actor: slicer
  entities:
  - entity: printer-file
    effect: changes
    from: Waiting for printer
    to: Ready to print
    facts:
    - Size
  - entity: printer
    effect: reads
    facts: []
  contexts:
    cli:
      place: slicer-hook
---

# Slicer file waits for a busy printer

## Trigger

A file is sliced while its printer is still busy.

## Outcome

The file reaches the printer as soon as it is free.
