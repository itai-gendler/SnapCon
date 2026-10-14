---
kind: primary
routes:
  web: Web
steps:
- text: Every 30 seconds, a printing printer's progress crosses one of the milestone percentages for the first time in this print
  kind: condition
  unattended: true
  entities:
  - entity: printer
    effect: reads
    facts:
    - Current print
  - entity: settings
    effect: reads
    facts:
    - Milestone updates
    - Milestone percentages
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product sends a milestone notification to every enabled service
  kind: product
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Current print
  - entity: settings
    effect: reads
    facts:
    - ntfy.sh alerts
    - Telegram alerts
    - Webhook alerts
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# A print crosses a milestone

## Trigger

A long print reaches 50%.

## Outcome

One message per milestone per print; milestones already passed when SnapCon starts are not sent.
