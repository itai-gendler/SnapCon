---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects a File, chooses Send, picks idle printers and which toolhead prints each color
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Colors
    - Sliced for
  - entity: printer
    effect: reads
    facts:
    - Name
    - Online
  - entity: toolhead
    effect: reads
    facts:
    - Number
    - Filament color
    - Material
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Regular user chooses Upload & Print
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Product uploads the File to each printer, applies the head mapping and the print options, and starts the print
  kind: product
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
  - entity: printer-file
    effect: creates
    to: Stored
    facts:
    - Name
    - Size
    - Colors
  - entity: printer
    effect: changes
    from: Idle
    to: Printing
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Product shows the result per printer and records each print start
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-printers
---

# Upload and print a file

## Trigger

A person starts a batch on several printers.

## Outcome

Each chosen printer is printing the file with the chosen toolheads.

## Decision points

### Print options

Does the printer force its default behavior?

- Force default behavior on → auto-leveling, flow calibration and time-lapse follow the printer's defaults
- Force default behavior off → the person confirms the print options for this job

## Edge cases

- A printer that is printing is refused; Upload is still possible.
- A Bambu Lab project prints the plate chosen in the dialog; plates other than 1 only on printers that can select a plate.
