# FAST Teensy 4.0 DIP Carrier Pin-Count Report

Symbol: `fast_teensy:FAST_Teensy40_DIP_Carrier`
Footprint: `fast_teensy:FAST_Teensy40_DIP_Carrier`

This FAST-specific carrier part exposes only the normal Teensy 4.0 side-header/socket contacts used by a plug-in module. It intentionally does not expose underside pads, SD pads, USB host pads, or test pads.

Symbol pin count: 28
Footprint pad count: 28

## Symbol Pins
- `GND1`
- `D0`
- `D1`
- `D2`
- `D3`
- `D4`
- `D5`
- `D6`
- `D7`
- `D8`
- `D9`
- `D10`
- `D11`
- `D12`
- `VIN`
- `GND2`
- `3V3`
- `D23`
- `D22`
- `D21`
- `D20`
- `D19`
- `D18`
- `D17`
- `D16`
- `D15`
- `D14`
- `D13`

## Footprint Pads
- `GND1`
- `D0`
- `D1`
- `D2`
- `D3`
- `D4`
- `D5`
- `D6`
- `D7`
- `D8`
- `D9`
- `D10`
- `D11`
- `D12`
- `VIN`
- `GND2`
- `3V3`
- `D23`
- `D22`
- `D21`
- `D20`
- `D19`
- `D18`
- `D17`
- `D16`
- `D15`
- `D14`
- `D13`

## Symbol-to-Footprint Mapping
| Symbol pin | Footprint pad |
|---|---|
| `GND1` | `GND1` |
| `D0` | `D0` |
| `D1` | `D1` |
| `D2` | `D2` |
| `D3` | `D3` |
| `D4` | `D4` |
| `D5` | `D5` |
| `D6` | `D6` |
| `D7` | `D7` |
| `D8` | `D8` |
| `D9` | `D9` |
| `D10` | `D10` |
| `D11` | `D11` |
| `D12` | `D12` |
| `VIN` | `VIN` |
| `GND2` | `GND2` |
| `3V3` | `3V3` |
| `D23` | `D23` |
| `D22` | `D22` |
| `D21` | `D21` |
| `D20` | `D20` |
| `D19` | `D19` |
| `D18` | `D18` |
| `D17` | `D17` |
| `D16` | `D16` |
| `D15` | `D15` |
| `D14` | `D14` |
| `D13` | `D13` |

## Phase 1 Required Pins
| Signal | Teensy carrier pin | ESP_AIR pin |
|---|---|---|
| `FAST_SPI_SCK` | `D13` | GPIO7 / D8 |
| `FAST_SPI_MOSI_ESP_TO_TEENSY_SDI` | `D12` | GPIO8 / D9 |
| `FAST_SPI_MISO_TEENSY_SDO_TO_ESP` | `D11` | GPIO9 / D10 |
| `FAST_SPI_CS` | `D10` | GPIO44 / D7 |
| `FAST_DATA_READY` | `D9` | GPIO43 / D6 |

54-pin Teensy symbol/footprint remains in use: NO. The schematic no longer references `teensy:Teensy4.0` or `teensy:Teensy40`.
