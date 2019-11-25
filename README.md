# EasyController2

A simple brushless (BLDC) sensored motor controller. Intended to drive electric vehicles such as electric bikes, skateboards, or Eco-Marathon vehicles. The controller can handle nominal power of about 1kW.

This controller was designed to fill a gap in publicly released motor controller designs. It is simple enough to serve as an introduction to power electronics, and to hopefully allow those unfamiliar with motors to get their feet wet. To this end, the controller is designed to be as simple and easy-to-understand as possible. Thus it lacks more complex features such as sensorless control or current-feedback control, however these features can be easily added with some modifications. This project is meant as a learning tool and a foundation to potentially build more complex designs from.

![Assembled Controller](/docs/side.jpg)

This project is a successor to the [2016 controller](http://www.duke-ev.org/blog/2016/11/27/the-2016-motor-controller) released on the DEV website. This design is dramatically easier to solder, more robust, and simpler, while still achieving the same functionality. We strongly encourage use of this new design.

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

## Design Improvements

The EasyController2 was designed with absolute simplicity in mind. It is meant to be as easy to understand as possible at the expense of additional features.

However, this design is very similar to the [world record motor controller](https://github.com/DukeElectricVehicles/dev-eagle/tree/master/Controller2019_Guinness) that powered DEV's vehicle [Eta to a Guinness World Record](https://pratt.duke.edu/about/news/duke-student-team-wins-second-guinness-world-record-vehicle-efficiency). Improvements to the world record design include:

* Lower quiescent power. The EasyController2 draws about 1 watt of quiescent power. As Eta's nomial power consumption was only 19 watts, this is too high. This can be improved with slower clocking of the microcontroller and more intelligent power supply design.
* Hybrid sensor/sensorless control. All electric vehicles need sensors for initial motor startup. However at high speed, hall sensors become noisy and do not provide as clean of trasitions as BEMF sensorless monitoring.
* Current feedback control. It is critical that the motor be run in the correct operating range to minimize resistance versus magnetic losses in the motor. This requires a current control loop, keeping the motor operating at the optimal power level.
* Synchronous switching. The EasyController2 only PWMs the high-side MOSFET, and in off times, the current flows through the low-side body diode. This is known as non-synchronous switching, and results in a roughly 0.7v loss during switch off-times. This loss becomes more significant at low duty cycles. Performing [synchronous switching](https://www.digikey.com/en/articles/techzone/2015/sep/what-you-need-to-know-about-synchronous-voltage-regulation) is only possible with current feedback control, and was thus omitted from the EasyController for simplicity. With synchronous switching and a current feedback loop, regen can be accomplished.

These improvements are only critical for those seeking to squeeze the last few percent of efficiency out of their powertrain. However, for most applications, the EasyController2 is more than sufficient. These improvements are left as an excercise to future electrical engineers to keep with the spirit of the Shell Eco-Marathon.

## Contact Us

This controller was designed by Patrick Grady from Duke Electric Vehicles. If you need help or clarification, please [send us a message on our website.](http://www.duke-ev.org/dev-contact-us)