---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user chooses Camera on a printer card
  kind: actor
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::camera
- text: The Product fetches a fresh image from the printer and shows it with when it was captured
  kind: product
  actor: view-only-user
  entities:
  - entity: printer
    effect: reads
    facts:
    - Camera
  contexts:
    web:
      place: web::fleet::camera
---

# View a printer's camera

## Trigger

A person wants to see how a print looks.

## Outcome

The latest image shows; Refresh fetches another.

## Edge cases

- In the Camera view, images refresh at the camera refresh interval, staggered across printers when that is on.
- A printer whose camera gives no image shows a placeholder that can be retried.
