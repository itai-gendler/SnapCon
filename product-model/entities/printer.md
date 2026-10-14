---
relations:
- entity: group
  verb: is-shared-with
  cardinality: many-to-many
- entity: toolhead
  verb: has
  cardinality: one-to-many
- entity: printer-queue
  verb: has
  cardinality: one-to-one
- entity: printer-file
  verb: stores
  cardinality: one-to-many
- entity: maintenance-entry
  verb: has
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server.js#buildPrinterRecord
- kind: code
  role: implementation
  target: connectors/index.js
- kind: code
  role: implementation
  target: server.js#probeCached
---

# Printer

One 3D printer SnapCon manages, reached directly on the local network through the connector for its brand. Its status, current print, temperatures and filament are what the printer itself reports.

## Information kept

- **Name** — how SnapCon and the slicer hook name it
- **Location** — where it stands
- **Brand** — taken from the connector, typed only for generic Klipper printers
- **Connector** — the printer family SnapCon drives it as: Snapmaker U1, generic Klipper, Creality, FlashForge, Bambu Lab (beta) or the simulator
- **Address** — IP address or hostname, and a port where the connector allows one
- **Credentials** — the access code or API token SnapCon uses with it, kept and never shown back
- **Serial number** — typed, or filled in from the printer on save
- **Purchase date** — starts its warranty
- **Power draw** — watts, for the energy cost estimate
- **Print defaults** — whether auto-leveling, flow calibration and time-lapse run before each print
- **Force default behavior** — whether Print uses the print defaults without asking for print options
- **Tags** — up to 20 short labels for filtering
- **Groups with access** — the groups that may see and use it; none means Everyone
- **Printer pool** — the Printer Pool it belongs to while Queue Management is on
- **Position** — its place in the fleet's manual order
- **Current print** — the file printing, progress, time remaining and layer, as the printer reports them
- **Temperatures** — bed and nozzle temperatures and their targets
- **Camera** — whether it has a camera, and its latest snapshot
- **Plate objects** — the objects of the current print, which one is printing and which are excluded
- **Total print hours** — from the printer's own print history
- **Warranty** — active, expiring or expired, twelve months from the purchase date
- **Next maintenance** — the soonest due date among its maintenance reminders
- **Online** — whether it answered its last check
- **Last seen** — when it last answered
- **Attention reasons** — overdue or upcoming maintenance and a queue that needs attention

## States

### Idle

Ready for a job; it may still show the last job until that is ejected.

### Printing

Running a print.

### Paused

A print is paused and can be resumed.

### Complete

The last print finished.

### Cancelled

The last print was cancelled.

### Error

The printer reports a fault or was emergency-stopped.

### Maintenance

Taken offline for maintenance: nothing is printed or dispatched on it until it is brought back online.
