---
entities:
- entity: settings
  shows:
  - G-code folder
  - Refresh interval
  - Currency
  - Filament cost
  - Electricity rate
  - Head mapping
  - Auto-match colors
  - Skip identical uploads
  - Overwrite different files
  - Upload while printing
  - Default language
  collects:
  - G-code folder
  - Refresh interval
  - Currency
  - Filament cost
  - Electricity rate
  - Head mapping
  - Auto-match colors
  - Skip identical uploads
  - Overwrite different files
  - Upload while printing
  - Default language
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js#publicCfg
---

# General settings

Where SnapCon finds sliced files, how often it checks printers, the cost rates used for estimates, the default language and what happens when files are sent to printers.
