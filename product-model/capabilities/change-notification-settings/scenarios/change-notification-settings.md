---
kind: primary
routes:
  web: Web
steps:
- text: The Admin turns on notifications, picks events and milestone percentages and enables one or more services with their topic, chat or webhook
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - Notifications
    - Notification events
    - Milestone updates
    - Milestone percentages
    - Include camera image
    - ntfy.sh alerts
    - Telegram alerts
    - Webhook alerts
  contexts:
    web:
      place: web::settings::notification-settings
- text: The Product saves them; the background watcher uses them from its next check
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - Notifications
    - Notification events
    - Milestone updates
    - Milestone percentages
    - Include camera image
    - ntfy.sh alerts
    - Telegram alerts
    - Webhook alerts
  contexts:
    web:
      place: web::settings::notification-settings
---

# Choose notifications

## Trigger

An Admin wants to hear when prints finish or fail.

## Outcome

Matching print events reach every enabled service.

## Edge cases

- Turning notifications off keeps every other choice.
- Regenerate gives a new random ntfy.sh topic, cutting off anyone subscribed to the old one.
- Bot tokens and webhook addresses are never shown back once saved; they can be replaced or cleared.
