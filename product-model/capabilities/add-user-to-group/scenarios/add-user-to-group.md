---
kind: primary
routes:
  web: Web
steps:
- text: The Admin opens Groups on a user account, checks a Group, and saves the row
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
- text: The Product adds the Group to the User account's groups
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

# Add a person to a group

## Trigger

A person joins a team.

## Outcome

The person sees the team's printers; a person in a group is no longer counted in Everyone.
