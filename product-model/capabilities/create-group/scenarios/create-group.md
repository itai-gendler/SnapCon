---
kind: primary
routes:
  web: Web
steps:
- text: The Admin opens Manage groups, types a name and chooses Add
  kind: actor
  actor: admin
  entities:
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product creates the Group and records it
  kind: product
  actor: admin
  entities:
  - entity: group
    effect: creates
    facts:
    - Name
    - Built-in
  contexts:
    web:
      place: web::settings::users-settings
---

# Create a group

## Trigger

A new team or customer needs its own printers.

## Outcome

The group can be given printers and people.
