---
kind: primary
routes:
  web: Web
steps:
- text: Every 30 seconds, a printer reports a new print SnapCon did not start
  kind: condition
  unattended: true
  entities:
  - entity: printer
    effect: reads
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product records the print start without a user and sends a Print started notification when that event is on
  kind: product
  entities:
  - entity: printer
    effect: changes
    from: Idle
    to: Printing
    facts: []
  - entity: settings
    effect: reads
    facts:
    - Notifications
    - Notification events
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# A print started at the printer

## Trigger

Someone starts a print on the printer's own screen.

## Outcome

The activity log and notifications include it like any other print.
