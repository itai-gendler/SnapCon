---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user picks a language in My language
  kind: actor
  actor: view-only-user
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Interface language
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product switches the interface to it and keeps it on the person's user account
  kind: product
  actor: view-only-user
  entities:
  - entity: user-account
    effect: changes
    facts:
    - Interface language
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Choose my interface language

## Trigger

A person wants SnapCon in another installed language.

## Outcome

SnapCon shows that language for this person from now on; choosing System default follows the installation's default language again.
