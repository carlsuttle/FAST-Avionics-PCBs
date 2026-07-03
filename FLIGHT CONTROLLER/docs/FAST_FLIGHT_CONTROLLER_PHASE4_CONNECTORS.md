# FAST Flight Controller Phase 4 Connectors

## Scope

Phase 4 adds schematic-only external connectors for IMU, CRSF receiver/radio, and `AS_GPS_XIAO_OUTBOARD`.

No PCB placement, routing, or board-outline work was performed.

## Confirmed Source References

Confirmed Teensy assignments came from:

- `C:\Users\dell\Platformio\esp32_crsf_telemetry\Teensy_ESP_AIR_GND_88cb9aa\Teensy\src\config.h`
  - lines 17-20: CRSF uses Teensy `Serial2`, `TX=8`, `RX=7`.
  - lines 24-27: GPS uses Teensy `Serial1`, `TX=1`, `RX=0`.
  - lines 30-32: I2C uses `SDA=18`, `SCL=19`.
- `C:\Users\dell\Platformio\esp32_crsf_telemetry\Teensy_ESP_AIR_GND_88cb9aa\Teensy\README.md`
  - lines 64-72 confirm CRSF and GPS serial assignments.
  - lines 75-76 confirm Teensy I2C pins.

Phase 5 updated the CRSF Teensy pins to match the newer local codebase:

- `C:\Users\dell\Platformio\Avionics Lab\include\config.h`
  - lines 22-23: `PIN_CRSF_RX = 15`, `PIN_CRSF_TX = 14`.

## J3 IMU

Symbol: `fast_common:PinHeader_1x06`

Footprint: `fast_common:PinHeader_1x06_P2.54mm`

| Pin | Net | Status |
| --- | --- | --- |
| 1 | `+5V_ESC_BEC` | connected |
| 2 | `GND` | connected |
| 3 | `IMU_SCL` | connected to U1 D19 / SCL |
| 4 | `IMU_SDA` | connected to U1 D18 / SDA |
| 5 | `IMU_INT` | provisional connector net only |
| 6 | `IMU_CS_OR_AUX` | provisional connector net only |

The IMU connector is powered from `+5V_ESC_BEC`, not `TEENSY_3V3`. The IMU breakout must provide Teensy-safe 3.3 V logic on `IMU_SCL` and `IMU_SDA`, or external level shifting is required.

`IMU_SCL` and `IMU_SDA` are connected because the Teensy I2C bus assignment is confirmed. No confirmed Teensy pins were found for `IMU_INT` or `IMU_CS_OR_AUX`, so those remain pending.

## J4 CRSF_RX

Symbol: `fast_common:PinHeader_1x04`

Footprint: `fast_common:PinHeader_1x04_P2.54mm`

| Pin | Net | Status |
| --- | --- | --- |
| 1 | `+5V_ESC_BEC` | connected |
| 2 | `GND` | connected |
| 3 | `CRSF_RX_TO_TEENSY` | connected to U1 D15 / RX3 |
| 4 | `CRSF_TX_FROM_TEENSY` | connected to U1 D14 / TX3 |

CRSF uses the newer `Serial3` assignment from the current local codebase: Teensy RX15 receives receiver TX, and Teensy TX14 drives receiver RX. The CRSF net names were preserved.

## J5 AS_GPS_XIAO_OUTBOARD

Symbol: `fast_common:PinHeader_1x06`

Footprint: `fast_common:PinHeader_1x06_P2.54mm`

The exact JST-XH 1x06 footprint remains pending; the current footprint is a provisional 2.54 mm through-hole header.

| Pin | Net | Status |
| --- | --- | --- |
| 1 | `+5V_ESC_BEC` | connected |
| 2 | `GND` | connected |
| 3 | `OUTBOARD_TX_TO_TEENSY_RX` | connected to U1 D0 / RX1 |
| 4 | `OUTBOARD_RX_FROM_TEENSY_TX` | connected to U1 D1 / TX1 |
| 5 | `OUTBOARD_SPARE1` | physically present, not routed to Teensy or ESP32 GPIO |
| 6 | `OUTBOARD_SPARE2` | physically present, not routed to Teensy or ESP32 GPIO |

`AS_GPS_XIAO_OUTBOARD` uses the previous GPS UART pins. The old GPS Teensy RX pin is D0, and the old GPS Teensy TX pin is D1.

Former offboard magnetometer I2C pins are now unused for J5. `IMU_SCL` and `IMU_SDA` are not routed to `AS_GPS_XIAO_OUTBOARD`.

## Preserved Nets

Phase 1 Teensy-to-ESP32 transport nets were preserved:

- `FAST_SPI_SCK`
- `FAST_SPI_MOSI_ESP_TO_TEENSY_SDI`
- `FAST_SPI_MISO_TEENSY_SDO_TO_ESP`
- `FAST_SPI_CS`
- `FAST_DATA_READY`

Phase 2 power nets were preserved:

- `+5V_ESC_BEC`
- `GND`
- `TEENSY_3V3`
- `ESP_3V3`

`TEENSY_3V3` and `ESP_3V3` remain separate.

Phase 3 SD module wiring was preserved:

- `ESP_SD_CS`
- `ESP_SD_SCK`
- `ESP_SD_MOSI`
- `ESP_SD_MISO`
- J2 VCC on `+5V_ESC_BEC`
- J2 GND on `GND`
