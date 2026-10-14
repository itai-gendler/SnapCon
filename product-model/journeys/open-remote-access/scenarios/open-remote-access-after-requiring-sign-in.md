---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Admin opens Remote Access, which says to turn on User Access Management first, and chooses Go to Users
  kind: actor
  actor: admin
  entities:
  - entity: remote-access
    effect: reads
    facts: []
  - entity: settings
    effect: reads
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::remote-access-settings
  capability: enable-remote-access
- text: The Product opens Users
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
  capability: enable-remote-access
- text: The Admin turns on Enable user access management with an Admin account and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  - entity: user-account
    effect: reads
    facts:
    - Role
  contexts:
    web:
      place: web::settings::users-settings
  capability: change-user-access-settings
- text: The Product requires sign-in
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
  capability: change-user-access-settings
- text: The Admin turns on Enable Remote Access and completes the verification
  kind: actor
  actor: admin
  entities:
  - entity: remote-access
    effect: reads
    facts:
    - Verification link
  contexts:
    web:
      place: web::settings::remote-access-settings
  capability: enable-remote-access
- text: The Product starts the tunnel and shows the public address
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: 'Off'
    to: Connected
    facts:
    - Public address
    - Verification link
    - Last connected
  contexts:
    web:
      place: web::settings::remote-access-settings
  capability: enable-remote-access
---

# Require sign-in, then enable Remote Access

## Trigger

An Admin of a SnapCon without sign-in wants to reach it from outside the local network.

## Outcome

SnapCon requires sign-in and is reachable at its public address.
