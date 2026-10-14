---
kind: primary
routes:
  web: Web
steps:
- text: The View-only user opens the file list and a folder
  kind: actor
  actor: view-only-user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  - entity: file
    effect: reads
    facts: []
  contexts:
    web:
      place: web::fleet::files
- text: The Product lists the folder's subfolders and sliced files, newest first or as sorted
  kind: product
  actor: view-only-user
  entities:
  - entity: folder
    effect: reads
    facts:
    - Name
  - entity: file
    effect: reads
    facts:
    - Name
    - Size
    - Modified
    - Full Spectrum
  contexts:
    web:
      place: web::fleet::files
- text: The View-only user selects a File
  kind: actor
  actor: view-only-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::fleet::files
- text: The Product reads the colors, print time, filament weight, thumbnail and the model it was sliced for from the File and estimates its cost from the cost rates
  kind: product
  actor: view-only-user
  entities:
  - entity: file
    effect: reads
    facts:
    - Colors
    - Estimated time
    - Filament weight
    - Thumbnail
    - Sliced for
    - Estimated cost
  - entity: settings
    effect: reads
    facts:
    - Currency
    - Filament cost
    - Electricity rate
  contexts:
    web:
      place: web::fleet::files
---

# Browse the G-code folder

## Trigger

A person looks for something to print.

## Outcome

The file's job details show, ready to send.

## Edge cases

- A .3mf project that was never sliced is marked not sliced and cannot be printed.
