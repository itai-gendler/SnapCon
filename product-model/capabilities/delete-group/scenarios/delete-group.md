---
kind: primary
routes:
  web: Web
steps:
- text: The Admin deletes a Group in Manage groups and confirms
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
- text: The Product deletes it and takes it off every printer and User account
  kind: product
  actor: admin
  entities:
  - entity: group
    effect: removes
  - entity: printer
    effect: changes
    facts:
    - Groups with access
  - entity: user-account
    effect: changes
    facts:
    - Groups
  contexts:
    web:
      place: web::settings::users-settings
---

# Delete a group

## Trigger

A team is disbanded.

## Outcome

Its printers and people that had only this group fall back to Everyone.

## Edge cases

- Everyone cannot be deleted.
