---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Send test for a service
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - ntfy.sh alerts
    - Telegram alerts
    - Webhook alerts
  contexts:
    web:
      place: web::settings::notification-settings
- text: The Product reads the first printer's live state and sends it as a test message, with its camera image when there is one
  kind: product
  actor: admin
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
    - Current print
    - Camera
  contexts:
    web:
      place: web::settings::notification-settings
---

# Send a test notification

## Trigger

An Admin checks a new destination works.

## Outcome

The message arrives, or the service's error shows.

## Edge cases

- With no printer, or the first printer offline, the test is refused with the reason.
