---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user chooses Switch to dark theme in the top bar
  kind: actor
  actor: view-only-user
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Theme
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product shows the dark theme and keeps it on the person's user account
  kind: product
  actor: view-only-user
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Theme
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Switch to the dark theme

## Trigger

A person prefers the other theme.

## Outcome

SnapCon shows the chosen theme now and at every later sign-in.

## Edge cases

- Without User Access Management the choice is kept only in that browser.
