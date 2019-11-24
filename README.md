# EasyController2

A simple brushless (BLDC) sensored motor controller. Intended to drive electric vehicles such as electric bikes, skateboards, or Eco-Marathon vehicles. The controller can handle nominal power of about 1kW.

This controller was designed to fill a gap in publicly released motor controller designs. It is simple enough to serve as an introduction to power electronics, and to hopefully allow those unfamiliar with motors to get their feet wet. To this end, the controller is designed to be as simple and easy-to-understand as possible. Thus it lacks more complex features such as sensorless control or current-feedback control, however these features can be easily added with some modifications. This project is meant as a learning tool and a foundation to potentially build more complex designs from.

![Assembled Controller](/docs/side.jpg)

This project is a successor to the [2016 controller](http://www.duke-ev.org/blog/2016/11/27/the-2016-motor-controller) released on the DEV website. This design is dramatically easier to solder, more robust, and simpler, which still achieving the same functionality. We strongly encourage use of the new design.

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

## Software Used

* PCB layout: [Eagle](https://www.autodesk.com/products/eagle/free-download)
* Compiler: [Arduino](https://www.arduino.cc/) with [PJRC Teensyduino add-on](https://www.pjrc.com/teensy/td_download.html)

## Assembly

This respository includes Gerber files which can be directly submitted to PCB manufacturers. We recommend Chinese manufacturers such as [AllPCB](https://www.allpcb.com/) or [JLCPCB](https://jlcpcb.com/). The repository also includes a Bill of Materials (BOM) with Digikey part numbers to order from.

Assembly is straightforward. However, it is recommended to cut the VIN-VUSB trace on the [underside of the Teensy](https://www.pjrc.com/teensy/card7b_rev1.pdf). Cutting the trace means that the Teensy can no longer be powered over USB. This is a safety procaution to prevent the controller feeding power backwards into your computer's USB port. 

## Contact Us

This controller was designed by Patrick Grady from Duke Electric Vehicles. If you need help or clarification, please [send us a message on our website.](http://www.duke-ev.org/dev-contact-us)