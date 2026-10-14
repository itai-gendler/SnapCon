---
kind: validation
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
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: User Access Management is off or no Admin account exists
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  - entity: admin
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: The Product refuses and offers Go to Users
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
---

# Remote Access needs sign-in first

## Trigger

An Admin tries to open a login-less SnapCon to the internet.

## Outcome

No tunnel starts.
