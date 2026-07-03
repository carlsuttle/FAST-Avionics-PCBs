# FAST Flight Controller Rev A, Phase 1 Pinmap

## Core Teensy <-> ESP_AIR Transport Mapping

```text
Teensy pin 13 -> ESP GPIO7  / D8   SCK
Teensy pin 12 -> ESP GPIO8  / D9   ESP MOSI -> Teensy slave SDI
Teensy pin 11 -> ESP GPIO9  / D10  ESP MISO <- Teensy slave SDO
Teensy pin 10 -> ESP GPIO44 / D7   CS
Teensy pin 9  -> ESP GPIO43 / D6   DATA_READY
```

## MOSI/MISO Direction Warning

ESP32-S3 is the SPI master.
Teensy 4.0 is the SPI slave.
Do not map MOSI/MISO by matching Teensy silkscreen labels.
Map by signal direction:
ESP MOSI drives Teensy slave SDI.
ESP MISO receives Teensy slave SDO.

## Phase 1 Net Labels

```text
FAST_SPI_SCK
FAST_SPI_MOSI_ESP_TO_TEENSY_SDI
FAST_SPI_MISO_TEENSY_SDO_TO_ESP
FAST_SPI_CS
FAST_DATA_READY
```

## Phase 1 Scope Notes

SD card pins are not wired in Phase 1.
Power input, regulation, and protection circuits are not designed in Phase 1.
PCB placement and routing are not part of Phase 1.
