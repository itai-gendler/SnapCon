---
availability:
- place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#notifyTick
- kind: code
  role: implementation
  target: server.js#sendEventNotification
- kind: code
  role: implementation
  target: webhookNotify.js#sendWebhook
---

# Watch prints

SnapCon's background watcher follows every printer whether or not a browser is open: it records prints that start, finish, fail or are cancelled, sends the chosen notifications, and moves queues on when a queued print ends.
