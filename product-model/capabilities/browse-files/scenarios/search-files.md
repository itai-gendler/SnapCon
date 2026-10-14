---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user types in the file search
  kind: actor
  actor: view-only-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
- text: The Product lists up to 300 matching sliced files from every subfolder, newest first
  kind: product
  actor: view-only-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
    - Modified
  contexts:
    web:
      place: web::fleet::files
---

# Search all subfolders

## Trigger

A person remembers part of a file name.

## Outcome

Matching files show wherever they are.
