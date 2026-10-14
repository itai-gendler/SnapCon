---
kind: primary
routes:
  web: Web
steps:
- text: The Admin changes the view options and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - Site name
    - Toolhead notation
    - Default view
    - Camera refresh interval
    - Stagger camera refresh
    - Card layout
  contexts:
    web:
      place: web::settings::view-settings
- text: The Product saves them and every dashboard follows them
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - Site name
    - Toolhead notation
    - Default view
    - Camera refresh interval
    - Stagger camera refresh
    - Card layout
  contexts:
    web:
      place: web::settings::view-settings
---

# Change view settings

## Trigger

An Admin adapts the dashboard to a large farm.

## Outcome

Everyone sees the new defaults.

## Edge cases

- Camera refresh is kept between 3 and 60 seconds to protect printer cameras.
