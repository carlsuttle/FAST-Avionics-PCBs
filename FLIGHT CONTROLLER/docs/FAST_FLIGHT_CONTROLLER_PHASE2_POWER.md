# FAST Flight Controller Rev A - Phase 2 Power

## Power Source

The board is powered from an external ESC/BEC that provides regulated `+5V_ESC_BEC` and `GND`.

No onboard regulator was added in Phase 2.
No PCB placement or routing was added in Phase 2.

## 5 V Distribution

`+5V_ESC_BEC` powers:

- J1 pin 1, `ESC_BEC_5V_IN`
- U1 Teensy 4.0 carrier `VIN`
- U2 XIAO ESP32-S3 `VBUS` / 5 V input
- C1, C2, C3 input capacitors
- TP1 test point

J1 pin 2 is connected to `GND`.

## Ground

`GND` connects:

- J1 pin 2
- U1 Teensy `GND1` and `GND2`
- U2 XIAO `GND`
- C1, C2, C3 return pins
- TP2 test point

## 3.3 V Rails

The Teensy and XIAO 3.3 V pins are treated as module-generated rails.

- U1 Teensy `3V3` is labeled `TEENSY_3V3` and connects only to TP3.
- U2 XIAO `3V3` is labeled `ESP_3V3` and connects only to TP4.

`TEENSY_3V3` and `ESP_3V3` are not connected together in Phase 2.
Neither 3.3 V rail is used as the main board power input.

## Input Capacitors

- C1: `100 uF >=10V bulk`, provisional footprint `fast_teensy:C_Radial_D5.0mm_P2.00mm`
- C2: `10 uF >=10V`, provisional footprint `fast_teensy:C_0805`
- C3: `100 nF`, provisional footprint `fast_teensy:C_0805`

All three capacitors connect from `+5V_ESC_BEC` to `GND`.

## Test Points

- TP1: `+5V_ESC_BEC`
- TP2: `GND`
- TP3: `TEENSY_3V3`
- TP4: `ESP_3V3`

## Reserved Pins

No SD card wiring was added in Phase 2.
ESP GPIO1 / D0, GPIO2 / D1, GPIO5 / D4, and GPIO6 / D5 remain reserved for Phase 3 SD card wiring and were not no-connected.

## Remaining ERC Status

ERC was run and saved to `docs/FAST_FLIGHT_CONTROLLER_PHASE2_ERC.rpt`.

Remaining electrical errors are unconnected pins left open for later phases or future design decisions. They were not hidden with no-connect markers.

The ERC report also contains footprint-link warnings for the local `fast_teensy` footprint nickname even though the project-local `fp-lib-table` contains the `fast_teensy` entry and the footprints exist under `${KIPRJMOD}/lib/footprints/fast_teensy.pretty`. These warnings are documented and not suppressed.