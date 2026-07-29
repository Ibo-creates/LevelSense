
<div align="center">

#  LevelSense

**An Iot baseed spirit level that measures tilt in all 3 axis with 0.2 degrees precision**

Measure pitch and roll in real time from any phone or computer through a built in web interface.



</div>

---

## Overview

Ive often seen my father use a spirit level, but I always thought how could that even be accurate and theres certainly a lot of parallex error. Triggering the small OCD tendency I decided to make Levelsense. 

Levelsense is a digital spirit level made for makers and engineers, mabye even used for industries if developed more. What levelsense do is measure the acceleration from the mpu6050 and convert this to roll and pitch angle using esp32c3 fast processing speed, which is then tranmistted live to a web page where the user can connect.

The user can select which axis to measure and the BG of the webpage turns greeen when its perfectly alligned.


---

## Features

-  Real time pitch and roll measurements
-  Builtin WiFi web dashboard
-  No mobile app required
-  Rechargeable LiPo battery
-  USB C charging

---

## Hardware

| Component | Part |
|-----------|------|
| Microcontroller | ESP32-C3 SuperMini |
| IMU | MPU6050 SMD |
| Battery | 3.7V Lipo |
| Charging | USB C LiPo Charger |
| Power Switch | Mini Slide Switch |

---

## Software

- Arduino Framework
- PlatformIO
- ESPAsyncWebServer
- MPU6050 Library

---



## Current Status

 **In Development**

This project was made for a hackclub event called macondo and its still in devlopement phase, as I require funding. 

*Things completed**

-Assembling the gadget and soldering components on the PCB to build the actual product itself.


---

## License

This project is licensed under the **MIT License**.

---

## Acknowledgements

This project is being developed as part of the **Hack Club Ship (Macondo)** program.
