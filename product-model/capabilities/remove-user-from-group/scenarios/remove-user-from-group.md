---
kind: primary
routes:
  web: Web
steps:
- text: The Admin opens Groups on a user account, unchecks a Group, and saves the row
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
    - Groups
  - entity: group
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product removes the Group from the User account's groups
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Groups
  - entity: group
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::users-settings
---

# Remove a person from a group

## Trigger

A person leaves a team.

## Outcome

The person stops seeing that team's printers; with no group left they belong to Everyone again.
