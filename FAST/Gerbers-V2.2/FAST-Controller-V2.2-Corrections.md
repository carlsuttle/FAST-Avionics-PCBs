# FAST Controller V2.2 production correction

Date: 2026-09-17

V2.2 supersedes the V2.1 Gerbers. Servo output connectors J8 through J15 now
use the confirmed standard order:

- pin 1: GND
- pin 2: +5V_ESC_BEC
- pin 3: PWM signal

The +5V_ESC_BEC copper spine was rerouted from pin 1 to pin 2, and both copper
zones were refilled. KiCad DRC reports zero violations. Its two remaining
unconnected-item messages are the pre-existing duplicate ground-zone artifacts
at the zone origin (20.5 mm, 20.5 mm), not physical pads or routed nets.

Production archive: `FAST-Controller-V2.2-Gerbers-2026-09-17.zip`.
