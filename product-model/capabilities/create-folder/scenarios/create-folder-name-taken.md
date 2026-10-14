---
kind: validation
routes:
  web: Web
steps:
- text: The Regular user enters a name that already exists, is empty, or contains a slash
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
- text: The Product refuses it and creates nothing
  kind: product
  actor: regular-user
  entities: []
  contexts:
    web:
      place: web::fleet::files
---

# Folder name refused

## Trigger

A person picks a name that cannot be used.

## Outcome

No folder is created and the reason shows.
