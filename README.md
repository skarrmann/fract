# Fract Keyboard

![Fract keyboard from a top view](images/fract-top-view.jpg)

![Fract keyboard from an edge side view](images/fract-edge-side-view.jpg)

Fract is a 34 key ortholinear keyboard, powered by a bluetooth-enabled Pro Micro compatible dev board.

It uses Choc v1 keyswitches with 18mm x 17mm spacing.

The goal of this design was to build a simple pocketable keyboard out of PCBs.

## Project structure

* [`gerbers`](gerbers): Gerber files for PCB manufacturing
* [`graphics`](graphics): Source assets for PCB silkscreen
* [`kicad`](kicad): KiCad project files (schematics and PCB designs)
* [`kicad-libraries`](kicad-libraries): KiCad components and footprints
* [`images`](images): Images for project documentation

## PCBs

**Each build uses two copies of the main PCB and two copies of the top plate PCB.**

The main PCB is used as the logical PCB. A second copy of the main PCB is used a bottom plate, by flipping it the long way and screwing it directly to the logical PCB.

Two copies of the top plate PCB cover the dev board and battery. Flip this PCB as well. It has a cutout which fits the reset button on the left, and the power switch on the right.

![Fract PCBs](images/fract-pcbs.jpg)

![Fract keyboard from a top angle view](images/fract-angle-top-view.jpg)

![Fract keyboard from a bottom angle view](images/fract-angle-bottom-view.jpg)

![Fract keyboard closeup of reset button and power switch](images/fract-reset-button-power-switch.jpg)

## Keyboard firmware

* ZMK
    * Fract shield definition is in [skarrmann's zmk-config](https://github.com/skarrmann/zmk-config)

## Bill of materials

Part | Purpose | Quantity | Notes
---- | ------- | -------- | ---------
Main PCB  | logical PCB, bottom plate | 2 | Send Gerber zip files to [JLCPCB](https://jlcpcb.com/)
Top plate PCB  | cover dev board and battery  | 2 | 
Bluetooth Pro Micro | Microcontroller board | 1 | nice!nano or SuperMini nRF52840
502040 LiPo Battery | Powers the wireless keyboard | 1 | JST PH 2.0 connector, ~5cm wire length
S2B-PH-K-S connector | JST PH 2.0 battery connector | 1 |
SS12D00, 5mm handle length | On/Off switch | 1 |
6mm x 6mm push button, 8mm total height | Reset button | 1 |
1N4148 SOD-123 | Diodes for keyboard row-column matrix | 34 |
Choc v1 Keyswitches |  | 34 |
Choc v1 Keycaps |  | 34 | Use keycaps which fit 18mm x 17mm spacing
M2 5mm screws | Screws PCBs together | 19 |
M2 6mm spacers | Spacers between logical PCB and top plates | 8 |
M2 nuts | Holds the top screws between the bottom plate and logical PCB | 3 |
[Peel-a-way Sockets and Pins](https://ringerkeys.com/collections/modders-tools/products/peel-a-way-sockets) | socket dev board to PCB | 2 strips of 12 pins/sockets | May use other low profile sockets which give less than 6 mm total height.

## PCB manufacturing settings

These are the manufacturing settings I used when ordering from JLCPCB:

* **Base Material**: FR4
* **Layers**: 2
* **Dimensions**: (whatever the gerber file specifies)
* **PCB Qty**: 5
* **Different Design**: 1
* **Delivery Format**: Single PCB
* **PCB Thickness**: 1.6
* **PCB Color**: Black
* **Silkscreen**: White
* **Surface Finish**: LeadFree HASL-RoHS
* **Outer Copper Weight**: 1 oz
* **Gold Fingers**: No
* **Confirm Production File**: No
* **Flying Probe Test**: Fully Test
* **Castellated Holes**: No
* **Mark on PCB**: Remove Mark

## Build tips

* Before starting, check if the PCBs are warped, and bend them to be perfectly flat before soldering.
* Make sure the diodes are oriented correctly, cathode on the side with the line! Once the keyswitches are soldered in, you won't be able to get to them anymore.
* Make sure the dev board is placed **components side up**. The pinout labels printed on the PCB should align with those printed on the dev board.
    * ![Fract keyboard build, dev board components side up](images/fract-dev-board-install.jpg)
* While soldering the the battery connector, reset button, and power switch, use tape to temporarily hold them in place. Solder just one leg of each of these components, make sure they are aligned correctly, and then solder the other legs. Clip the legs of the power switch since they are longer than the bottom plate.
    * ![Fract keyboard build, battery connector, reset button, power switch](images/fract-reset-button-power-switch-install.jpg)
* Don't plug in the battery until you're done soldering everything! **MAKE SURE THE BLACK WIRE (-) IS ON TOP AND THE RED WIRE (+) IS ON BOTTOM, OR YOU'LL FRY YOUR DEV BOARD!** Use tape to secure the battery and its wires.
    * ![Fract keyboard build, battery taped in place](images/fract-battery-install.jpg)

## KiCad project notes

The top plate was generated with the [Horizon Board Producer KiCad plugin](https://github.com/skarrmann/horizon#kicad-project-notes).

## Revision history

* Fract 1.0 (2024-10-16)
    * Initial Choc switch PCB design