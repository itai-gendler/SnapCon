---
references:
- kind: code
  role: implementation
  target: server.js#publicUser
- kind: code
  role: implementation
  target: auth.js
---

# User account

A person's account while User Access Management is on: who they are, how they sign in, their role, their groups and their own display choices.

## Information kept

- **First name** — optional
- **Last name** — optional
- **Login name** — 2 to 32 letters, digits, _ . or -, unique ignoring case
- **Email** — optional; where one-time codes go when they are sent by email
- **Phone** — optional
- **Role** — Admin, Regular or View Only
- **One-time code sign-in** — whether the person signs in with a one-time code instead of a password
- **Password** — at least 8 characters, kept only as a hash and never shown
- **Groups** — the groups the person belongs to; none means Everyone
- **Theme** — light or dark
- **Interface language** — the person's own language, or the system default
