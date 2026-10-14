---
scope: Fleet monitoring and control, file sending, Queue Management, maintenance, users and groups, notifications, activity log and Remote Access behavior of the SnapCon server, its printer connectors and its web app.
method: Static inspection of source, README, CLAUDE.md, locale strings and tests at the pinned commit; nothing was run.
covered:
- description: 'Express server: printer, file, print, queue, user, group, settings, maintenance, notification and Remote Access routes and the background watcher.'
  paths:
  - server.js
- description: Sign-in, sessions, one-time codes and role guards.
  paths:
  - auth.js
- description: Group-based printer visibility.
  paths:
  - groupAccess.js
- description: Queue state machine, persistence and pool migration.
  paths:
  - queue/
- description: 'Printer connectors: probing, print control, uploads, toolheads, cameras and discovery.'
  paths:
  - connectors/
- description: Activity log storage and pruning.
  paths:
  - audit/
- description: Remote Access tunnel service.
  paths:
  - remote-access/
- description: Sliced-file metadata, thumbnails and 3MF reading.
  paths:
  - parser.js
  - threemf.js
  - public/printer-identity.js
- description: Slicer hook token, webhook notifications and file path containment.
  paths:
  - notifyToken.js
  - webhookNotify.js
  - pathSafety.js
  - configLoader.js
- description: 'Web app: fleet dashboard, file list, Send dialogs, Print Farm view, health, maintenance, sign-in and Settings.'
  paths:
  - public/app.js
  - public/index.html
  - public/i18n.js
  - public/error-codes.js
- description: Shipped interface translations.
  paths:
  - locales-default/
- description: Product documentation.
  paths:
  - README.md
  - PrintCard.md
exclusions:
- description: Automated tests, fixtures and test helpers.
  paths:
  - test/
  - fixtures/
  - connector-compat-test.js
- description: Build, packaging, container and launcher files.
  paths:
  - .github/
  - Dockerfile
  - docker-compose.yml
  - .dockerignore
  - .gitignore
  - package.json
  - package-lock.json
  - start-mac-linux.sh
  - start-windows.bat
  - config.example.json
  - LICENSE
- description: Developer diagnostics, spikes and capture tools.
  paths:
  - spike/
  - capture-proxy.js
  - bambu-probe.js
  - .archon/
- description: Styling, fonts and icons.
  paths:
  - public/style.css
  - public/fonts/
- description: Design notes, research and screenshots.
  paths:
  - docs/
  - U1_FIRMWARE_DEPLOY_BRIEF.md
  - RELEASE_NOTES.md
  - CLAUDE.md
- description: Sample G-code folder content.
  paths:
  - gcode/
unmapped:
- description: 'Model Library: indexing of local and network folders into Models, its review queue, decisions, print history and its own permissions, specified separately in docs/library-design.md.'
  paths:
  - library/
  - public/library.js
  - public/library-raw.html
  - public/library-diagnostics.html
- description: Network-safe file access layer shared by the Library and the G-code folder.
  paths:
  - netfs/
- description: 'Firmware tab: reading firmware versions and deploying Snapmaker U1 firmware images.'
  paths:
  - connectors/snapmaker-u1-firmware.js
  - connectors/firmwareImage.js
- description: Logs, camera and G-code sync from printers to local folders.
  paths:
  - sync/
- description: Language editor for installed translations.
  paths:
  - locales.js
- description: Update check against published releases.
  paths:
  - updateCheck.js
limitations: []
---

# Coverage
