---
kind: primary
routes:
  web: Web
steps:
- text: The Regular user chooses E-Stop on a printer card and confirms
  kind: actor
  actor: regular-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::fleet-dashboard
- text: The Product sends the emergency stop to the printer and records it
  kind: product
  actor: regular-user
  entities:
  - entity: printer
    effect: changes
    from: Printing
    to: Error
    facts:
    - Current print
  contexts:
    web:
      place: web::fleet::fleet-dashboard
---

# Emergency stop a printer

## Trigger

Something on a printer is going physically wrong.

## Outcome

The printer halts and reports a fault until it is restarted at the machine.

## Edge cases

- On a printer whose firmware does not halt on the command, E-Stop is unavailable and the card says to cancel or cut power.
