# FAST Flight Controller Phase 3 SD Module

## Design

J2 is a plug-in SD-card breakout module, not a raw microSD socket. The module is intended to be soldered into the FAST Flight Controller PCB so that its daughterboard stands vertically, perpendicular to the main PCB.

J2 uses the project-local symbol `fast_common:SD_Module_1x06` and the provisional footprint `fast_common:SD_Module_1x06_Vertical_Daughterboard`.

## Header Pin Order

The module label order, from top to bottom, is:

| Pin | Label |
| --- | --- |
| 1 | CS |
| 2 | SCK |
| 3 | MOSI |
| 4 | MISO |
| 5 | VCC |
| 6 | GND |

## Electrical Connections

| J2 pin | Net | ESP_AIR connection |
| --- | --- | --- |
| 1 CS | `ESP_SD_CS` | U2 GPIO2 / D1 |
| 2 SCK | `ESP_SD_SCK` | U2 GPIO5 / D4 |
| 3 MOSI | `ESP_SD_MOSI` | U2 GPIO6 / D5 |
| 4 MISO | `ESP_SD_MISO` | U2 GPIO1 / D0 |
| 5 VCC | `+5V_ESC_BEC` | External regulated 5 V BEC rail |
| 6 GND | `GND` | Common ground |

VCC currently connects to `+5V_ESC_BEC` because the selected style of SD breakout module appears to include onboard 3.3 V regulation and interface circuitry. Do not change J2 VCC to `ESP_3V3` unless the exact physical module is later confirmed to require a 3.3 V input.

## Mechanical Notes

The physical module, header side, pin-1 position, board-facing side, and clearance envelope must be visually checked against the provisional footprint before PCB layout.

Mechanical support or retention may be needed because the SD module stands vertically and can apply leverage to the six-pin soldered header during card insertion, removal, vibration, or impact.
