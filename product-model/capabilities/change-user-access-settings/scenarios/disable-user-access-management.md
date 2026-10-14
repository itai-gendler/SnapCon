---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns off Enable user access management and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
- text: Remote Access is off
  kind: condition
  entities:
  - entity: remote-access
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product stops requiring sign-in
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
---

# Stop requiring sign-in

## Trigger

A farm on a trusted network drops sign-in.

## Outcome

Everyone who opens SnapCon acts as an Admin; accounts and groups are kept for later.

## Edge cases

- While Remote Access is on, turning sign-in off is refused until Remote Access is turned off.
