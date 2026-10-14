---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses New folder in the current folder and enters a name
  kind: actor
  actor: regular-user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
- text: The Product creates the Folder
  kind: product
  actor: regular-user
  entities:
  - entity: folder
    effect: creates
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
---

# Create a folder

## Trigger

A person wants to organize sliced files.

## Outcome

The new folder appears in the file list.
