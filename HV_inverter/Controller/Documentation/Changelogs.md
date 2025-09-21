# v2.8

## Schematics:

* Changed the power conversion flow to: Battery+/Aux --> 12V(relays) --> 4.0V(modem) --> 3.3V(system)
* Replaced the 3.3V LDO from AMS1117-3.3 --> AP2114H-3.3

## Board:

* Changes following the schematics.



# v2.7

## Schematics:

* Added fiducial markers to the bottom side of the board.
* Replaced ATA6562 with TCAN3404.
* Removed the 5V LDO.
* Added a connector for connnecting the Link+ with the flyback capacitor on SSR board v1.11.

## Board:

* Changes following the schematics.
* Fixed the Ffab and Bfab layers of all the custom footprints.

# v2.6

## Schematics:

* Added fiducial marks.
* Changed the SIM diodes to a cheaper alternative.
* Reconnected the SIM holder body (shield) from SIM\_GND --> BMS\_GND.
* Replaced the main fuse from 1A fast-acting to 2.5A (withstands inrush, and is cheaper).

## Board:

* Changes following the schematics.

# v2.5

## Schematics:

* Disconnected VDD\_REF of the modem from the 4V supply, because it generates 2.8V for IO interface.
* Added 1K resistors in the UART Tx path from modem to microcontroller, and a voltage dividers of (1K, 5.6K) in the UART Tx path from microcontroller to modem.
* Added ESD protection diodes along the SIM lines.

## Board:

* Changes following the schematics.

# v2.4

## Schematics:

* Changed vendor for 40MHz crystal in favor of lower price, and replaced the supporting capacitors to 9pF.
* Accelerometer's unused ADC pins connected to ground.
* SIM\_DATA pulled-up to SIM\_VCC using 100K 0402.
* Connected VDD\_REF of the modem to 3.3V instead of 4V.

## Board:

* Changes following the schematics.
* Optimised the Bluetooth antenna trace as per calculations... removed the series component.
* Added the missing ground-pour on layer2 of the IoT region.
* Repaired the CAN and UART traces to remove the 180deg turns.

# v2.3

## Schematics:

* Added a 4.7K pullup for SSR NTC.

## Board:

* Changes following the schematics.

# v2.2

## Schematics:

* Replaced the resistor across the Source-Drain of the shutdown FET, with a 10uF capacitor for holding the shutdown signal until the BMS is fully switched OFF.

## Board:

* Changes following the schematics.

# v2.1

## Schematics:

* Changed ESP32-S2 to ESP32 (same as IoT-2G) for Bluetooth.

## Board:

* Changes following the schematics.

# v2.0

## Schematics:

* Added the circuit from AvIoT\_2G for integration with the BMS. Additions include: LIS3DHTR, MC60CB, and supporting circuits.
* Added a buck converter for 12V --> 4.0V \& 3A to power the modem.

## Board:

* Changes following the schematics.
* Increased the board size to accommodate the additional circuits.

# v1.11

## Schematics:

* Replaced ESP32-C6 (ESP8684) and S32K142 with a single ESP32-S2FH4 for cost reduction.

## Board

* Changes following the schematics.

# v1.10

## Schematics:

* Changed the 5V regulator to IL1117-5.0
* Changed the input capacitors of 3.3V and 5.0V regulators to 22uF 25V

## Board:

* Changes following the schematics.

# v1.9

## Schematics:

* Changed the main harness connector from 2.50mm to 3.0mm pitch, due to its wide availability.
* Changed the value of R100, 10K -> 100K, because otherwise the microcontroller seems to be drawing a large portion of the opto-isolator current at bootup using charger.
* Changed the Buck converter LM5168F->LM5012 and enabled the required additional capacitors at the input and output.
* Changed the optocoupler power supply 3.3V->5.0V (coming from CMU1) inorder to enable the buck converter.
* Added a 22uF electrolytic capacitor as bootstrap for the FET gate driver.
* Changed the arrangement of power supply components as follows: Fuse -> reverse protection diode -> bulk capacitor -> EMC inductor -> supply switch resistors -> supply (Buck / 12V).
  This is done inorder to ensure that the fuse isn't blown while charging the bulk capacitor, and the same capacitor falls in the loop for both inputs of the power supply (buck / 12V).

## Board:

* Changes following the schematics.

# v1.8

## Schematics:

* Corrected the vendor info for the flasher and UART connectors.

## Board:

* No changes here.

# v1.7

## Schematics:

* Added extra pin for Link- at the connector of SSR.
* Added a 10nF 100V capacitor between the Link+ and Link- pin of the opto-isolator of the charger detection.

## Board:

* Changes following the schematics.

# v1.6

## Schematics:

* Removed the board detection feature, as the board won't power-up using a charger, unless the Link- is connected to the main board via the bottom plate.

## Board:

* Changes following the schematics.

# v1.5

## Schematics:

* Added a diode in the charger detection circuit, inorder to prevent the LDO voltage from reflecting at the Charger\_detection\_pin.

## Board:

* Changes following the schematics.

# v1.4

## Schematics:

* Changed the main harness connector to molex nano-fit 2x6 pins for adding the input for ignition and auxiliary battery's ground.

## Board:

* Changes following the schematics.
* Increased the board width by 0.75mm, additional space for the new connector.
* Increased the via size to 0603 for Link+ and Link- lines.

# v1.3

## Schematics:

* Brought the I2C pull-ups closer to the isolator, and changed the values to 1.5K.
* Changed the footprint for C37 to 0603.
* Corrected the footprints of U4, U7, U30, C67.
* Changed the diode D3 to the same as D2.
* Changed the part of L2 to fit in 5mm x 5mm area.
* Changed the part of PS1 to fit in SOT-89.
* Changed R102 to 240K in order to get ~1.65V as reference voltage out of the OPAMP.
* Changed the part of R255, R256, R125, R126 to 0402.
* Changed C167 to through-hole for cost reduction, and to higher voltage (>150V) for tolerance to 1.25x of 120V (input to the buck).
* Removed the transistor (Q4) that switches ON the first CMU, the microcontroller will directly control the shutdown.
* Removed the Alert circuit from the CMU.
* Added a fuse at the highest cell terminal of each CMU.
* Added a fuse at the input of BMS buck.
* Created 66.6K using three 200K in parallel near the input of opto-isolator for charger detection circuit (based on the test observations with 30V to 120V), and modified the charger detection circuit to take 3.3V from CMU\_1.
* Added a 10K at the input of charger detection GPIO of the microcontroller.
* The SSR control pin now also controls the contactor.
* Order PS1, D3, L2, R255, R256, R125, R126, R56, R60, R137, R139, R102, F1, F2, F3, R110, R141

## Board:

* Changes following the schematics.

# v1.2

## Schematics:

* Changed the balancer MOSFETs to the ones with VGS\_th < 1.0V for conducting the required currents at low cell voltages.
* Removed the ferrite beads along the CAN lines after studying the document: [Common Mode Chokes in CAN Networks: Source of Unexpected Transients](https://www.ti.com/lit/an/slla271/slla271.pdf), and instead added 1.2nF capacitors at the bus lines for noise suppression above 1Mbaud rate.

## Board:

* Changes following the schematics.

# v1.1

## Schematics:

* Added vendors for all the components.

## Board:

* Added labels for Cells and NTC connections.

# v1.0

## Schematics:

* Derived out of 24s board.
* This one has a low cost AFE (MP2787) for sensing the cell voltages and NTC voltages as well as performing passive balancing using external FETs.
* Supports cells from 17s to 32s.
* Changed the CAN termination from split-type to single resistor.

## Board:

* First commit.
