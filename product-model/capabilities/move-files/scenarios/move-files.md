---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user selects files with Shift or Ctrl and drags them onto a Folder
  kind: actor
  actor: regular-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
- text: The Product moves each File that is not already there and has no namesake in the target, and reports any it skipped
  kind: product
  actor: regular-user
  entities:
  - entity: file
    effect: changes
    facts: []
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
---

# Move files into a folder

## Trigger

A person tidies the G-code folder.

## Outcome

The files are in the target folder; any that could not move are listed with the reason.
