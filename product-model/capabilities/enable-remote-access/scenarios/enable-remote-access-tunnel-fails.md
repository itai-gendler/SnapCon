---
kind: edge
routes:
  web: Web
steps:
- text: The Admin turns on Enable Remote Access for an installation verified before
  kind: actor
  actor: admin
  entities:
  - entity: remote-access
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: The Product provisions and starts the tunnel
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: 'Off'
    to: Starting
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: The tunnel cannot start or the public address does not answer, so the Product shows the error and keeps retrying
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: Starting
    to: Error
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
---

# Tunnel cannot start

## Trigger

The tunnel's stored credential is lost or the network blocks it.

## Outcome

Remote Access shows Error with the reason; Restart tunnel and the tunnel log help diagnose it.
