---
id: snapcon
summary: 'Local-first fleet management for 3D print farms built around the Snapmaker U1: monitor and control every printer, send files with toolhead mapping, run per-printer job queues in printer pools, and scope access by group.'
category: 3d-print-farm-management
tags:
- 3d-printing
- print-farm
- fleet-management
- local-first
license: MIT
languages:
- en
- es
limitations:
- SnapCon talks to every printer directly on the local network and needs no cloud service; printer activity leaves it only through Remote Access and the notification and sign-in services an Admin turns on.
- With User Access Management off, everyone who opens SnapCon acts as an Admin; sign-in, roles and printer groups apply only while it is on.
- 'Each printer keeps its own queue, and a Printer Pool clears the bed by hand: after every queued print a person confirms the bed is clear before the next job starts.'
- Print status, toolhead filament and temperatures are read from the printers themselves; SnapCon never invents a reading a printer does not report.
- SnapCon creates folders, uploads and moves files in the G-code folder only when a person asks; it never deletes them.
references:
- kind: doc
  role: intent
  target: README.md
- kind: doc
  role: context
  target: CLAUDE.md
- kind: code
  role: implementation
  target: server.js
---

# SnapCon

SnapCon is one local web application for running a farm of 3D printers, built primarily for the Snapmaker U1 with experimental connectors for other printer brands. Operators watch every printer on a fleet dashboard with live status, toolhead filament and camera snapshots, pause, resume, cancel or stop prints, heat beds across the fleet, exclude objects mid-print and keep maintenance records. They send sliced files from a watched G-code folder to one or many printers, choosing which toolhead prints each color, or hand files to a slicer hook that stages them on a printer. With Queue Management on, every printer belongs to a Printer Pool and keeps an ordered queue that SnapCon dispatches by itself, with a bed-clear confirmation between prints and attention states when something goes wrong. Optional User Access Management adds sign-in, three roles and groups that decide which printers each person sees; notifications, an activity log and optional Remote Access round it out.

## Intent

SnapCon provides a single interface for monitoring, controlling, and managing multiple printers without requiring printer activity or operational data to be sent to a third-party cloud service. It is intended primarily for Snapmaker U1 owners and farm operators who need a practical, centralized, and locally controlled way to manage multiple printers from one interface.
