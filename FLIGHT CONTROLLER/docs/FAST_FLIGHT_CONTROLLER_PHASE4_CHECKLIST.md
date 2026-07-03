# FAST Flight Controller Phase 4 Checklist

- [x] J3 IMU connector added
- [x] J4 CRSF connector added
- [x] J5 AS_GPS_XIAO_OUTBOARD connector added
- [x] J3 power pin correct: pin 1 = `+5V_ESC_BEC`
- [x] J3 is not connected to `TEENSY_3V3`
- [x] J3 ground pin correct: pin 2 = `GND`
- [x] J4 power pin correct: pin 1 = `+5V_ESC_BEC`
- [x] J4 ground pin correct: pin 2 = `GND`
- [x] J5 power pin correct: pin 1 = `+5V_ESC_BEC`
- [x] J5 ground pin correct: pin 2 = `GND`
- [x] J5 UART connected to old GPS UART pins: D0/RX1 and D1/TX1
- [x] Old offboard magnetometer I2C not routed to J5
- [x] J5 pins 5/6 preserved as spares and not routed to ESP32 GPIOs
- [x] No existing Teensy to ESP32 transport nets changed
- [x] No SD module nets changed
- [x] `+5V_ESC_BEC` preserved
- [x] `TEENSY_3V3` and `ESP_3V3` remain separate
- [x] Netlist export passed
- [x] ERC run
- [x] Remaining ERC errors explained in `FAST_FLIGHT_CONTROLLER_PHASE4_ERC.rpt`
- [x] No PCB placement or routing performed

## Pending

- [ ] Final J5 connector footprint selection, preferably JST-XH 1x06 2.50 mm if that is the selected physical connector
- [ ] Confirm whether `IMU_INT` should connect to a Teensy GPIO
- [ ] Confirm whether `IMU_CS_OR_AUX` should connect to a Teensy GPIO
