# EasyController2

A simple brushless (BLDC) sensored motor controller. Intended to drive electric vehicles such as electric bikes, skateboards, or Eco-Marathon vehicles. The controller can handle nominal power of about 1kW.

This controller was designed to fill a gap in publicly released motor controller designs. It is simple enough to serve as an introduction to power electronics, and to hopefully allow those unfamiliar with motors to get their feet wet. To this end, the controller is designed to be as simple and easy-to-understand as possible. Thus it lacks more complex features such as sensorless control or current-feedback control, however these features can be easily added with some modifications. This project is meant as a learning tool and a foundation to potentially build more complex designs from.

![Assembled Controller](/docs/side.jpg)

## Specifications
* 15v-60v operation
* 20A continuous current, 40A burst (more with heatsinking)
* All through-hole design. Easy to solder!
* Socket for automotive fuse
* Automatic hall sensor identification
* Extremely simple code. <200 lines with comments
* Duty-cycle control
* Teensy 3.2 microcontroller
* L6387E gate drivers
* IRFB7730 MOSFETS
* BOM cost of 70 USD
* Totally open source

## Schematic

![Schematic](/docs/schematic.png)

## Board

![Board](/docs/board.png) ![Board](/docs/top.jpg)

## Software

* PCB layout: [Eagle](https://www.autodesk.com/products/eagle/free-download)
* Compiler: [Arduino](https://www.arduino.cc/) with [PJRC Teensyduino add-on](https://www.pjrc.com/teensy/td_download.html)
