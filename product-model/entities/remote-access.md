---
singleton: true
domain: remote-access
references:
- kind: code
  role: implementation
  target: remote-access/RemoteAccessService.js
---

# Remote Access

This installation's managed tunnel that gives SnapCon a public HTTPS address without opening any port.

## Information kept

- **Public address** — the HTTPS address it is reached at
- **Verification link** — the one-time verification page for a new installation
- **Last connected** — when the tunnel last connected

## States

### Off

No tunnel runs; the public address is not reachable.

### Verification needed

Waiting for the one-time verification of this installation.

### Starting

Provisioning and starting the tunnel.

### Connected

Reachable at its public address.

### Error

Could not start; the reason is shown.
