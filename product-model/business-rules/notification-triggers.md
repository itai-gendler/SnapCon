---
appliesTo:
- type: capability
  id: watch-prints
- type: entity
  id: settings
  facts:
  - Notifications
  - Notification events
  - Milestone updates
  - Milestone percentages
references:
- kind: code
  role: implementation
  target: server.js#notifyTick
---

# Notifications follow the chosen events, checked every 30 seconds

With notifications on and at least one service ready, a print starting, pausing, failing or being cancelled, and finishing each sends a message when its event is chosen, and each chosen milestone sends one per print. Prints started at the printer count too.
