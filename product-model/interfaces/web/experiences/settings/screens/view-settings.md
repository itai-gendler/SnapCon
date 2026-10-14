---
entities:
- entity: settings
  shows:
  - Site name
  - Toolhead notation
  - Default view
  - Camera refresh interval
  - Stagger camera refresh
  - Card layout
  collects:
  - Site name
  - Toolhead notation
  - Default view
  - Camera refresh interval
  - Stagger camera refresh
  - Card layout
- entity: user-account
  shows:
  - Interface language
  collects:
  - Interface language
references:
- kind: code
  role: implementation
  target: public/app.js
---

# View settings

How the fleet is displayed: site name, toolhead numbering, the default view, the card layout, camera refresh, and the Admin's own interface language.
