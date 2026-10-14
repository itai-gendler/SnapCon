---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects a File, chooses Send, picks printers and, when asked, which toolhead prints each color
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Colors
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
- text: The Regular user chooses Upload
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
- text: The Product uploads the File to each printer, showing progress, and applies the head mapping and print options
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
    to: Sending
    facts:
    - Name
    - Size
    - Colors
  - entity: printer
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::send-to-printers
- text: The Product stages it as ready to print on each printer card and records the upload
  kind: product
  actor: regular-user
  entities:
  - entity: printer-file
    effect: changes
    from: Sending
    to: Ready to print
    facts: []
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::send-to-printers
---

# Upload a file to printers

## Trigger

A person prepares printers for a batch to start later.

## Outcome

Each printer card shows the file as ready to print, one click from printing, in every open tab.

## Decision points

### Head mapping

Does the Send dialog ask which toolhead prints each color?

- Head mapping on → the person assigns colors to toolheads, with the closest toolhead color suggested when Auto-match colors is on
- Head mapping off → colors go to toolheads in order, T1 to T1

### Same file already there

Does the printer already have a file of this name?

- Identical copy and Skip identical uploads on → nothing is sent and the card says the file was already there
- Different file and Overwrite different files on, or no copy → the file is sent and replaces any namesake

## Edge cases

- A printer that is printing receives the file at once when Upload while printing is on.
- Several colors may share one toolhead.
