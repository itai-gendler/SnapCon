---
singleton: true
references:
- kind: code
  role: implementation
  target: server.js#publicCfg
---

# SnapCon settings

The one set of settings an installation keeps.

## Information kept

- **G-code folder** — the folder SnapCon watches for sliced files
- **Refresh interval** — how often printers are checked, 1 to 60 seconds
- **Currency** — for cost estimates
- **Filament cost** — price per spool
- **Electricity rate** — price per kWh
- **Head mapping** — whether the color-to-toolhead choice shows when sending
- **Auto-match colors** — whether the closest toolhead color is suggested, otherwise T1 to T1
- **Skip identical uploads** — whether a file the printer already has byte for byte is not sent again
- **Overwrite different files** — whether a different file of the same name on the printer is replaced
- **Upload while printing** — whether Upload sends to a printing printer at once instead of waiting
- **Site name** — shown next to the logo
- **Toolhead notation** — T0 to T3 instead of 1 to 4
- **Default view** — the view SnapCon opens in
- **Camera refresh interval** — seconds between camera grid refreshes
- **Stagger camera refresh** — whether camera refreshes are spread over the interval
- **Card layout** — New or Classic
- **Default language** — for anyone who has not chosen their own
- **Notifications** — whether notifications are sent at all
- **Notification events** — which of print started, paused, error or failure, and finished send one
- **Milestone updates** — whether progress milestones send one
- **Milestone percentages** — the progress percentages that do
- **Include camera image** — whether a snapshot is attached
- **ntfy.sh alerts** — whether notifications go to an ntfy.sh topic, and the topic
- **Telegram alerts** — whether notifications go to a Telegram chat, with the bot and chat
- **Webhook alerts** — whether notifications go to a webhook, its address and Discord or generic JSON format
- **User access management** — whether signing in is required
- **One-time code delivery** — email, ntfy.sh or Telegram, and where codes go
- **Email sender** — the email service key and from address for one-time codes
- **Log retention** — days the activity log keeps, 90 by default
- **Queue management** — whether Queue Management is on
