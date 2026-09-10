# FAST Controller V2.1 — Production Corrections

Date: 2026-09-10

This note records faults discovered after manufacture of the original V2 board and the corrections incorporated into the V2.1 design files and manufacturing package.

## 1. CRSF receiver ground at J4

### Error

J4 pin 2 was assigned to GND in the schematic, but its copper-pour connection formed an isolated island. KiCad therefore showed the pad surrounded by GND-coloured copper even though it had no conductive path to the main board ground. The original DRC report's zone-to-zone unconnected warnings were incorrectly treated as harmless.

### V2.1 correction

The assembly requires an insulated wire link from **J4 pin 2 to TP3**. Both points are through-hole and TP3 is a confirmed main-ground point. The instruction is also printed on the bottom silkscreen:

`FIT INSULATED LINK: J4-2 TO TP3`

On already-manufactured V2 boards, fit the same link. J7/J8 grounds may provide another receiver-ground path in normal installation, but they are not a substitute for making the CRSF connector ground independently correct.

### Verification

Continuity test before power-up: J4 pin 2 to TP3 and to the Teensy GND pins must measure approximately zero ohms.

## 2. Logic-supply isolation diodes D1 and D2

### Error

D1 and D2 were electrically reversed. Their old orientation allowed the +5V_LOGIC rail to feed back toward the BEC source rails, opposite to the intended isolation behaviour.

### V2.1 correction

Both diode symbols and both PCB footprints have been reversed while retaining PMEG4050EP Schottky diodes:

- D1: anode to +5V_PM_BEC; cathode to +5V_LOGIC.
- D2: anode to +5V_ESC_BEC; cathode to +5V_LOGIC.

Either BEC can now supply +5V_LOGIC, while +5V_LOGIC cannot back-power either BEC rail. Observe the V2.1 footprint polarity marking when fitting the parts.

### Verification

With the board unpowered, diode-test mode should conduct from each BEC source rail toward +5V_LOGIC and block in the reverse direction.

## 3. Watchdog multiplexer-select default state

### Error

The ADM706 watchdog output drives MUX_SELECT, but the line had no discrete pull-down. Its fail-safe state could therefore be uncertain while the watchdog output or its supply was inactive.

### V2.1 correction

R30, 10 kΩ, 0805 hand-solder footprint, has been added from MUX_SELECT to GND. The resistor is connected directly to the existing MUX_SELECT trace and forces the receiver-PWM path to its safe default state when the watchdog is not actively driving the line.

### Verification

With the board unpowered, measure approximately 10 kΩ from MUX_SELECT to GND. During a watchdog timeout, confirm that MUX_SELECT is low and the CD74HCT157 multiplexers select the receiver PWM inputs.

## Manufacturing-package status

The corrected manufacturing output is identified as **FAST Controller V2.1**. Do not send the earlier V2 Gerber ZIP for a new production run. The V2.1 package includes the updated diode orientation, R30 pads and markings, board version marking, and the mandatory J4-to-TP3 insulated-link assembly instruction.

KiCad's final geometry check reports zero clearance, short-circuit, footprint, and silkscreen violations. It intentionally retains two unconnected-zone findings for the J4 ground island because the connection is completed by the specified insulated assembly link rather than PCB copper.

## Required pre-flight checks

1. Confirm the J4 pin 2 to TP3 link is installed and insulated.
2. Confirm D1 and D2 polarity by diode test.
3. Confirm +5V_ESC_BEC and +5V_PM_BEC are isolated from one another.
4. Confirm R30 measures 10 kΩ from MUX_SELECT to GND.
5. Power the board from each BEC source separately and verify +5V_LOGIC.
6. Test watchdog timeout and all eight receiver/Teensy servo-output paths before flight.
