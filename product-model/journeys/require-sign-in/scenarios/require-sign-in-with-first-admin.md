---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Admin turns on Enable user access management
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
  capability: change-user-access-settings
- text: No user account exists, so the Product asks for the first Admin's login name and password
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts: []
  contexts:
    web:
      place: web::settings::users-settings
  capability: change-user-access-settings
- text: The Admin enters a login name and password and chooses Create admin
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - Login name
  contexts:
    web:
      place: web::settings::users-settings
  capability: create-user
- text: The Product creates the User account with the Admin role
  kind: product
  actor: admin
  entities:
  - entity: user-account
    effect: creates
    facts:
    - First name
    - Last name
    - Login name
    - Email
    - Phone
    - Role
    - One-time code sign-in
    - Password
    - Groups
  contexts:
    web:
      place: web::settings::users-settings
  capability: create-user
- text: The Admin saves the settings
  kind: actor
  actor: admin
  entities:
  - entity: settings
    effect: reads
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
  capability: change-user-access-settings
- text: The Product requires sign-in from then on
  kind: product
  actor: admin
  entities:
  - entity: settings
    effect: changes
    facts:
    - User access management
  contexts:
    web:
      place: web::settings::users-settings
  capability: change-user-access-settings
---

# Turn on sign-in and create the first Admin

## Trigger

An Admin of a SnapCon without accounts turns on Enable user access management.

## Outcome

The first Admin account exists and SnapCon requires sign-in.
