---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Remove Remote Access and confirms
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
- text: The Product stops the tunnel, deletes the installation's remote setup and records it
  kind: product
  actor: admin
  entities:
  - entity: remote-access
    effect: changes
    from: Connected
    to: 'Off'
    facts:
    - Public address
    - Verification link
  contexts:
    web:
      place: web::settings::remote-access-settings
---

# Remove Remote Access

## Trigger

An Admin retires remote use for good.

## Outcome

Nothing of the remote setup remains; it cannot be undone.
