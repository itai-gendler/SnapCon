---
kind: primary
routes:
  web: Web
steps:
- text: The Admin picks email, ntfy.sh or Telegram for one-time codes, enters its details and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - One-time code delivery
    - Email sender
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product saves them
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - One-time code delivery
    - Email sender
  contexts:
    web:
      place: web::settings::users-settings
---

# Set one-time code delivery

## Trigger

Accounts will sign in with one-time codes.

## Outcome

Codes go through the chosen service.

## Edge cases

- Telegram codes use the bot set up for notifications.
- Test OTP sends a test code with the values on screen.
