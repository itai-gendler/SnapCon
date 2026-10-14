---
entities:
- entity: settings
  shows:
  - User access management
  - One-time code delivery
  - Email sender
  collects:
  - User access management
  - One-time code delivery
  - Email sender
- entity: user-account
  shows:
  - First name
  - Last name
  - Login name
  - Email
  - Phone
  - Role
  - One-time code sign-in
  - Groups
  collects:
  - First name
  - Last name
  - Login name
  - Email
  - Phone
  - Role
  - One-time code sign-in
  - Password
  - Groups
- entity: group
  shows:
  - Name
  - Built-in
  collects:
  - Name
references:
- kind: code
  role: implementation
  target: public/app.js
- kind: code
  role: implementation
  target: server.js
---

# User settings

User Access Management and one-time code delivery, every user account with its role, sign-in method and groups, and the groups themselves.
