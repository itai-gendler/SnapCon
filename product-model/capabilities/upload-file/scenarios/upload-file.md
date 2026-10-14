---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses upload in the file list and picks sliced files on their computer
  kind: actor
  actor: regular-user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  - entity: file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::files
- text: The Product saves each one into the current Folder without overwriting anything
  kind: product
  actor: regular-user
  entities:
  - entity: file
    effect: creates
    facts:
    - Name
    - Size
    - Modified
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
---

# Upload a sliced file

## Trigger

A file was sliced on another computer.

## Outcome

The files are in the G-code folder, ready to send.

## Edge cases

- A file of the same name already there is refused, never replaced.
- Only .gcode, .gco, .g, .gx and .3mf files are accepted.
