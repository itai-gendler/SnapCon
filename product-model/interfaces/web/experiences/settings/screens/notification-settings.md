---
entities:
- entity: settings
  shows:
  - Notifications
  - Notification events
  - Milestone updates
  - Milestone percentages
  - Include camera image
  - ntfy.sh alerts
  - Telegram alerts
  - Webhook alerts
  collects:
  - Notifications
  - Notification events
  - Milestone updates
  - Milestone percentages
  - Include camera image
  - ntfy.sh alerts
  - Telegram alerts
  - Webhook alerts
references:
- kind: code
  role: implementation
  target: public/app.js
---

# Notification settings

Whether notifications are on, which print events and progress milestones send one, whether a camera image is attached, and the ntfy.sh, Telegram and webhook destinations with a test for each.
