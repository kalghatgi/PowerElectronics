# v1.2

## 2D model

* No changes here.

## 3D model

* Created a model for the toroidal core.
* Created an assembly of the planar transformer with toroidal core and winding.

## Schematics

* Added more pins for secondary current transfer.

## Board

* Changed the winding arrangement from El-->toroidal type.
* Reduced the number of layers from 12-->6.
* Increased the trace width of secondary winding to 9mm for lowering the power dissipation at 10A currents.

## Simulation

* Nothing here.


# v1.1

## 2D model

* Reduced the core's cross-section area for reducing the inductance.

## Schematics

* Switched to KiCAD 9
* Added a symbol for connector pins, inorder to introduce a Net-name for the traces.

## Board

* Imported the design using .dxf out of the 3D modelling software.
* Scaled upto 10 layers for primary, and 2 layers for secondary.

## Simulation

* Imported ODB++ model for simulation of inductance and the switching frequency response.


# v1.0

## 2D model

* Designed a flyback transformer for 1200Vdc --> 2.1Vdc, 10Adc, using 3D modelling softwares.

## Schematics

* Nothing here.

## Board

* Imported the design using .dxf out of the 3D modelling software.
* Scaled upto 10 layers for primary, and 2 layers for secondary.
