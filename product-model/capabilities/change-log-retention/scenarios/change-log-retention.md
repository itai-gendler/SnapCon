---
kind: primary
routes:
  web: Web
steps:
- text: The Admin enters a number of days in Keep logs for and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - Log retention
  contexts:
    web:
      place: web::settings::logs
- text: The Product keeps it; older entries are pruned daily
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - Log retention
  contexts:
    web:
      place: web::settings::logs
---

# Change log retention

## Trigger

An Admin needs a longer or shorter history.

## Outcome

Entries older than the retention disappear at the next daily pruning.
