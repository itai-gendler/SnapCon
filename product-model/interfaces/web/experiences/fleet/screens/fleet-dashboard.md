---
entities:
- entity: printer
  shows:
  - Name
  - Location
  - Brand
  - Tags
  - Current print
  - Temperatures
  - Camera
  - Online
  - Last seen
  - Attention reasons
  - Position
- entity: toolhead
  shows:
  - Number
  - Filament color
  - Material
- entity: printer-file
  shows:
  - Name
  - Size
- entity: printer-queue
  shows:
  - Jobs waiting
  - Paused
  - Stopped
- entity: settings
  shows:
  - Site name
  - Toolhead notation
  - Default view
  - Card layout
- entity: user-account
  shows:
  - First name
  - Theme
  - Interface language
entryPoints:
- web: /
- web: /orca/<printer name>
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# Fleet dashboard

Every printer the person may see, as full cards, compact cards, a camera grid or a sortable list: status, current print, temperatures, the filament in each toolhead, a staged file ready to print, queue state and anything that needs attention, with search, status and tag filters and the printer controls the person's role allows.
