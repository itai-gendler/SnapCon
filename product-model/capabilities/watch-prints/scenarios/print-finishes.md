---
kind: primary
routes:
  web: Web
steps:
- text: Every 30 seconds, a printer that was printing now reports its print complete
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
- text: The Product records the finished print with its time and its filament and cost estimate from the current rates
  kind: product
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Complete
    facts: []
  - entity: settings
    effect: reads
    facts:
    - Filament cost
    - Electricity rate
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: While notifications and the Print finished event are on, the Product sends the printer's name and what it printed to every enabled service, with a camera image when chosen
  kind: product
  entities:
  - entity: settings
    effect: reads
    facts:
    - Notifications
    - Notification events
    - Include camera image
    - ntfy.sh alerts
    - Telegram alerts
    - Webhook alerts
  - entity: printer
    effect: reads
    facts:
    - Name
    - Current print
    - Camera
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# A print finishes

## Trigger

A print ends while nobody watches.

## Outcome

The activity log holds the finished print and the chosen services got a message.

## Edge cases

- One service failing does not stop the others.
