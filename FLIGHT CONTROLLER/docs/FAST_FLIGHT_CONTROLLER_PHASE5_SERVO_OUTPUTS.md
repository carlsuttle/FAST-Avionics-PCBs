# FAST Flight Controller Phase 5 Servo Outputs

## Scope

Phase 5 adds schematic-only RC servo output connectors. No PCB placement, routing, trace sizing, or board-outline work was performed.

Servo connector standard for every output:

| Pin | Net |
| --- | --- |
| 1 | `+5V_ESC_BEC` |
| 2 | `GND` |
| 3 | PWM signal |

The first five channels have two physical connectors each. The A/B connectors for a channel share the same PWM signal net.

Servo power is `+5V_ESC_BEC`. Servo current must be considered during PCB layout, including trace width, connector current rating, and BEC current capacity.

## Source Pin Map

The Teensy PWM pin assignment comes from:

- `C:\Users\dell\Platformio\Avionics Lab\include\teensy_pinmap.h`
  - line 7: `kTeensyPwmAileronPin = 2`
  - line 8: `kTeensyPwmElevatorPin = 3`
  - line 9: `kTeensyPwmThrottlePin = 4`
  - line 10: `kTeensyPwmRudderPin = 5`
  - line 11: `kTeensyPwmFlapsPin = 7`
  - line 12: `kTeensyPwmSparePin = 8`

The newer CRSF pin assignment comes from:

- `C:\Users\dell\Platformio\Avionics Lab\include\config.h`
  - line 22: `PIN_CRSF_RX = 15`
  - line 23: `PIN_CRSF_TX = 14`

CRSF net names are preserved, but the Teensy pins are updated to D15/D14 so D7/D8 can be used for PWM outputs.

## Servo Connectors

| Channel | Function | Connector | Signal net | Teensy pin |
| --- | --- | --- | --- | --- |
| CH1 | Aileron | `J6A` / `J6B` | `SERVO_CH1_PWM` | U1 D2 |
| CH2 | Elevator | `J7A` / `J7B` | `SERVO_CH2_PWM` | U1 D3 |
| CH3 | Throttle | `J8A` / `J8B` | `SERVO_CH3_PWM` | U1 D4 |
| CH4 | Rudder | `J9A` / `J9B` | `SERVO_CH4_PWM` | U1 D5 |
| CH5 | Flaps | `J10A` / `J10B` | `SERVO_CH5_PWM` | U1 D7 |
| CH6 | Spare PWM | `J11` | `SERVO_CH6_PWM` | U1 D8 |

Symbol used for every servo connector: `fast_common:PinHeader_1x03`

Footprint used for every servo connector: `fast_common:PinHeader_1x03_P2.54mm`

Do not use `TEENSY_3V3` or `ESP_3V3` for servo power.

Netlist export passed. KiCad reports an annotation warning because the requested connector references use the `J6A`/`J6B` style rather than ending in a digit.
