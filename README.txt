This project adds a data field to your Garmin bike computer, built using Garmin Connect IQ (CIQ).

It allows your bike computer to connect to a Forumslader V5 or V6 (a generator-based
battery/charge controller for e-bikes and dynamo-powered bikes) using Bluetooth Low Energy
(BLE), and to display and record its live telemetry - battery status, charge/discharge
current, dynamo output, speed, distance, and more - directly on your Garmin cycling computer.
The data field connects automatically, keeps reconnecting in the background if the BLE link
drops, and requires no companion phone app.

FEATURES
========

Display Fields:
The following Forumslader metrics can be assigned to any of the 4 display fields (see
"Configure Display Fields" below):
- Trip Energy (Wh) - energy generated since the last trip reset
- Temperature (deg C) - Forumslader external temperature sensor (if installed)
- Dynamo Power (W) - instantaneous power delivered by the dynamo
- Generator Gear - active gear/step of the dynamo regulator
- Distance / Odometer - total distance derived from wheel rotations
- Battery Current (A) - signed charge (+) / discharge (-) current
- Electrical Load (W) - power drawn by connected consumers (lights, USB, etc.)
- Speed - current speed derived from wheel rotation
- Battery Level (%) - remaining battery capacity
- Day Distance / Tour Distance - resettable Forumslader distance counters
- Consumed Energy (Wh) - energy consumed since the current activity started
- Estimated Range - projected remaining range, based on consumption and distance
  covered since the current activity started
- BLE Diagnostic Dashboard - live BLE connection health (see below)

Depending on the "Scroll Fields" setting, either all 4 configured fields are shown
concatenated on one line, or one field at a time, cycling on tap (see "Field Rotation").

Battery/charge indicator:
A small battery icon (with a charging-bolt overlay while actively charging) is drawn in the
corner of the data field once a Forumslader is actually connected. It reflects the current
capacity (red <20%, orange 20-30%, green >30%) and the charging state (charge/discharge/trickle/standby).

BLE Diagnostic Dashboard:
The "BLE Diagnostic" field provides real-time BLE connection diagnostics, useful for
troubleshooting an unstable connection:
- D: Disconnect Count - total number of BLE disconnects since the data field started
- E: Checksum Errors - total number of payload checksum errors since the data field started
- B: BLE Throughput - bytes per second currently received

Field Rotation:
With "Scroll Fields" enabled (default), only one of the 4 configured fields is shown at a
time; tap the data field to cycle to the next configured field. With "Scroll Fields"
disabled, all 4 configured fields are shown concatenated on a single line, separated by
a middle dot (·).

Battery Capacity Calculation:
Remaining battery capacity can be computed either from coulomb counting (accumulated
charge/discharge current, more accurate but requires an initial full-charge calibration)
or from battery voltage (simpler, less precise) - selectable via the "Coulomb Count" setting.

Alerts:
When enabled, the app raises on-screen alerts for:
- Battery Level Below 20%
- Short Circuit
- System Interrupt

Auto Trip Reset:
When enabled, the Forumslader's trip counters are automatically reset once the connected
activity's timer starts running, so every recorded activity starts with a clean trip energy
baseline without requiring a manual reset on the Forumslader itself.

Lock to Device:
When enabled, the app remembers and reconnects only to the specific Forumslader it last
paired with, instead of connecting to the first matching device found during a scan -
useful if more than one Forumslader-equipped bike may be nearby.

Recording (FIT):
All display fields can additionally be recorded to your activity's FIT file via 4
independently configurable Recording Fields (separate from the 4 display fields above),
so you can review Forumslader telemetry later in Garmin Connect or any FIT-compatible
analysis tool - even for metrics you don't keep visible on the data field itself.

Configure Display and Recording Fields:
1. Open the app settings menu (gear icon) on the Garmin, or use Garmin Connect Mobile App
2. Select "Show Fields" or "Recording Fields"
3. Choose any Forumslader metric for each field (or "Off" to leave it unused)

Connectivity:
The app scans for and connects to a Forumslader automatically once the data field is active
- no manual pairing step is required. If the BLE connection drops after a device has been
successfully connected, the app waits for the device to automatically reconnect rather than
immediately rescanning; if no device has been paired yet (or reconnection fails repeatedly),
it falls back to an active rescan with increasing backoff between attempts.

You're welcome to raise issues and open pull requests to support development of this app.

You can download the current release of this app from Garmin's IQ store.

BUILD
=====

This project now uses a single build target and always builds from manifest.xml.
The app UUID used for releases is f37ce83f-ad98-4708-9741-fa4fa15c0d69.

The file manifest.monetized.xml is kept in the repository as a legacy reference only
and is not used by the active build configuration.
