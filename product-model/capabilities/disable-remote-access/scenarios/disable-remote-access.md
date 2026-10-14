---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns off Enable Remote Access and confirms
  kind: actor
  actor: admin
  entities:
  - entity: remote-access
    effect: reads
    facts:
    - Public address
  contexts:
    web:
      place: web::settings::remote-access-settings
- text: The Product stops the tunnel and records it
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: Connected
    to: 'Off'
    facts: []
  contexts:
    web:
      place: web::settings::remote-access-settings
---

# Disable Remote Access

## Trigger

Remote use is no longer needed.

## Outcome

The public address stops answering at once.
