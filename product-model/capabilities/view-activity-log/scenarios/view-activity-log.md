---
kind: primary
routes:
  web: Web
steps:
- text: The Admin opens Logs, picks a date range, a category and a search text and chooses Filter
  kind: actor
  actor: admin
  entities:
  - entity: activity-log-entry
    effect: reads
    facts:
    - Category
  contexts:
    web:
      place: web::settings::logs
- text: The Product lists the matching Activity log entries newest first, more on Load more
  kind: product
  actor: admin
  entities:
  - entity: activity-log-entry
    effect: reads
    facts:
    - Time
    - Category
    - Event
    - User
    - Printer
    - Detail
  contexts:
    web:
      place: web::settings::logs
---

# Review the activity log

## Trigger

An Admin investigates what happened to a print.

## Outcome

The entries show who did what to which printer, even for printers since renamed or removed.
