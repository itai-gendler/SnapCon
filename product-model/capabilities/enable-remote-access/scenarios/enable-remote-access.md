---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns on Enable Remote Access
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
- text: User Access Management is on and an Admin account exists
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  - entity: user-account
    effect: reads
    facts:
    - Role
  - entity: admin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: The Product registers this installation and shows the verification link
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: 'Off'
    to: Verification needed
    facts:
    - Verification link
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: The Admin opens the verification page and completes it
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
- text: The Product provisions and starts the tunnel and shows the public address once it answers
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: Verification needed
    to: Connected
    facts:
    - Public address
    - Last connected
  contexts:
    web:
      place: web::settings::remote-access-settings
---

# Enable Remote Access for the first time

## Trigger

An Admin wants to reach the farm from a phone away from home.

## Outcome

SnapCon is reachable at its public address; everyone signs in there with their account.

## Edge cases

- Re-enabling after Disable reuses the verified installation and skips verification.
