---
kind: primary
routes:
  web: Web
steps:
- text: The Admin renames a Group in Manage groups
  kind: actor
  actor: admin
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
    - Built-in
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product saves the new name and records it
  kind: product
  actor: admin
  entities:
  - entity: group
    effect: changes
    facts:
    - Name
  contexts:
    web:
      place: web::settings::users-settings
---

# Rename a group

## Trigger

A team is renamed.

## Outcome

Everywhere shows the new name.

## Edge cases

- Everyone cannot be renamed.
