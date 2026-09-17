# FAST Controller V2 as-built record — 2026-09-17

The manufactured FAST Controller V2 board has been installed and bench-tested
in the aircraft. The production PCB remains the V2.1 design in this directory.

## As-built corrections

- PMEG4050EP isolation diodes are installed in the corrected direction so the
  ESC BEC or power-module BEC can power `5V_LOGIC`, without `5V_LOGIC`
  back-feeding either BEC input.
- A field link connects the watchdog output/test point to CD74HCT157E select.
- A 10 kOhm pull-down from mux select to ground is fitted so loss of watchdog
  drive selects receiver PWM.
- The CRSF 5 V pin is intentionally unconnected. The receiver and servo rail
  are powered through the PWM harness: pin 5 ground and pin 6 ESC-BEC 5 V on
  each six-pin JST-XH receiver connector.
- The CRSF ground pad on its connector is not relied upon for receiver return;
  receiver ground is present through the PWM harness. A wire link to nearby
  ground test point TP3 remains the available repair if a dedicated CRSF
  ground is required.

## Confirmed connector/pin mapping

- J8 is servo output channel 1.
- J15 is servo output channel 8.
- Board channel 8 (`TEENSY_PWM8_RAW`) is routed to Teensy D1, not Teensy D8.
- Teensy D8 is board channel 7 (`TEENSY_PWM7_RAW`).
- Flaps are therefore implemented in firmware as CRSF channel 8 -> Teensy D1
  -> board channel 8 -> J15.

## Integration result

All installed servo channels were confirmed operational from Teensy control,
and receiver PWM failover was confirmed through the hardware multiplexers.
IMU, ESP_AIR, ESP_OUTBOARD, CRSF, SD recording, file listing, and flight-log
replay were also verified after installation.

