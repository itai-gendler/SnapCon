---
kind: validation
routes:
  cli: Command line
steps:
- text: The Slicer runs the hook with a name no printer in SnapCon has
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
- text: The Product answers that the name is unknown and stages nothing
  kind: product
  actor: slicer
  entities: []
  contexts:
    cli:
      place: slicer-hook
---

# Slicer names an unknown printer

## Trigger

The printer name in the slicer's post-processing step is mistyped.

## Outcome

The hook fails with the reason; nothing is sent.

## Edge cases

- The hook also fails when SnapCon is not running on that machine.
