---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user chooses Logout in the top bar
  kind: actor
  actor: view-only-user
  entities:
  - entity: user-account
    effect: reads
    facts:
    - First name
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product ends the session and records the sign-out
  kind: product
  actor: view-only-user
  entities: []
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Sign out

## Trigger

A person is done with SnapCon on a shared screen.

## Outcome

The session is gone and the login form shows again.
