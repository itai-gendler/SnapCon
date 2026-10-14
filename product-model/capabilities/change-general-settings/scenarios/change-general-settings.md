---
kind: primary
routes:
  web: Web
steps:
- text: The Admin changes where SnapCon looks for sliced output, the refresh interval, cost rates or sending options in General and saves
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
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
  contexts:
    web:
      place: web::settings::general-settings
- text: The chosen location is reachable and the refresh interval is between 1 and 60 seconds
  kind: condition
  entities:
  - entity: settings
    effect: reads
    facts:
    - G-code folder
    - Refresh interval
  contexts:
    web:
      place: web::settings::general-settings
- text: The Product saves the settings, applies them at once and records what changed
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
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
  contexts:
    web:
      place: web::settings::general-settings
---

# Change general settings

## Trigger

An Admin sets SnapCon up or adjusts it.

## Outcome

The new settings apply without a restart.

## Decision points

### Electricity rate lookup

Does the Admin look the rate up by ZIP code?

- A US ZIP code is entered → SnapCon fills in that area's residential rate from the public utility-rate database
- No ZIP code → the Admin types the rate

## Edge cases

- While a location is typed, SnapCon says whether it exists and holds sliced files.
- A refresh interval under 2 seconds is warned about for larger farms.
