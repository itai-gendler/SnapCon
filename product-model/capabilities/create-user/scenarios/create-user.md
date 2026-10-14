---
kind: primary
routes:
  web: Web
steps:
- text: The Admin chooses Add User, enters a login name, names, email, phone and role, and a password or OTP login, and saves
  kind: actor
  actor: admin
  entities:
  - entity: user-account
    effect: reads
    facts:
    - First name
    - Last name
    - Login name
    - Email
    - Phone
    - Role
    - One-time code sign-in
  contexts:
    web:
      place: web::settings::users-settings
- text: The Product creates the User account and records it
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
---

# Create a user account

## Trigger

Someone new needs access.

## Outcome

The person can sign in with their role.
