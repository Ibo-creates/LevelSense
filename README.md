# LevelSense
An Iot baseed spirit level that measures tilt in all 3 axis with 0.2 dgrees precision.
<div align="center">

# 📐 LevelSense

**A portable Wi-Fi digital spirit level powered by the ESP32-C3.**

Measure pitch and roll in real time from any phone or computer through a built-in web interface.

<!-- Add a project banner here later -->
<!-- ![Banner](docs/images/banner.png) -->

</div>

---

## Overview

LevelSense is a compact electronic spirit level designed for makers, engineers, and hobbyists. Instead of relying on a traditional bubble level, it uses an MPU6050 IMU to accurately measure orientation and streams the data to a responsive web dashboard hosted directly on the ESP32-C3.

The goal is to create an affordable, rechargeable, and easy-to-build digital level that anyone can assemble using open-source hardware and software.

---

## Features

- 📐 Real-time pitch & roll measurements
- 🌐 Built-in Wi-Fi web dashboard
- 📱 No mobile app required
- 🔋 Rechargeable LiPo battery
- ⚡ USB-C charging
- 🖨️ Custom 3D-printed enclosure
- 🔧 Open-source hardware and firmware

---

## Hardware

| Component | Part |
|-----------|------|
| Microcontroller | ESP32-C3 SuperMini |
| IMU | MPU6050 |
| Battery | 3.7V LiPo |
| Charging | USB-C LiPo Charger |
| Power Switch | Mini Slide Switch |

---

## Software

- Arduino Framework
- PlatformIO
- ESPAsyncWebServer
- MPU6050 Library

---

## Repository Structure

```
firmware/      ESP32 firmware
hardware/      PCB, schematic, BOM
enclosure/     3D CAD files (STEP/STL)
docs/          Documentation & images
```

---

## Current Status

🚧 **In Development**

### Completed

- ✅ Firmware architecture
- ✅ Web dashboard
- ✅ Wi-Fi communication
- ✅ Project planning

### In Progress

- ⏳ PCB Design
- ⏳ Enclosure Design
- ⏳ Hardware Assembly
- ⏳ Testing & Calibration
- ⏳ Documentation

Hardware prototyping and validation will begin after the required components are available.

---

## Roadmap

- [x] Design project architecture
- [x] Develop firmware
- [ ] Design PCB
- [ ] Assemble prototype
- [ ] Test sensor accuracy
- [ ] Design enclosure
- [ ] Optimize battery life
- [ ] Release Version 1.0

---

## License

This project is licensed under the **MIT License**.

---

## Acknowledgements

This project is being developed as part of the **Hack Club Ship (Macondo)** program.
