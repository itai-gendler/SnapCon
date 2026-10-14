---
appliesTo:
- type: capability
  id: dispatch-queued-job
  contexts:
  - place: web::fleet
references:
- kind: code
  role: implementation
  target: server.js#attemptQueueDispatch
- kind: code
  role: implementation
  target: queue/QueueEngine.js#claimTransition
---

# A queued job dispatches only to a free printer whose queue is idle, not paused or stopped, with its file unchanged

Before sending, SnapCon fingerprints the file again; a changed or missing file stops the queue for a person's decision. A folder that does not answer keeps the job waiting in place.
