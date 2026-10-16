# AML Sumo Robot

An autonomous sumo robot developed for robot-sumo competition, combining opponent detection, motion control, custom electronics, and mechanical design.

[![Watch the AML Sumo Robot demonstration](https://img.youtube.com/vi/gYu9niBVdmw/hqdefault.jpg)](https://www.youtube.com/watch?v=gYu9niBVdmw)

*Competition robot demonstration — [watch on YouTube](https://www.youtube.com/watch?v=gYu9niBVdmw).*

## Project overview

Robot sumo requires a small autonomous robot to locate its opponent, stay inside the ring, and make rapid movement decisions. This project brings those responsibilities together in an Arduino-compatible firmware application alongside the corresponding KiCad board design and mechanical model.

The firmware targets an **ATmega2560 (Arduino Mega 2560)**, as specified in the PlatformIO configuration. The source separates motor control, laser distance sensing, infrared sensing, IMU handling, and the local input interface into dedicated modules.

## Hardware and firmware

| Area | Implementation in this repository |
| --- | --- |
| Microcontroller | ATmega2560 / Arduino framework |
| Firmware build system | PlatformIO |
| Distance sensing | VL53L0X-related libraries and laser-sensor module |
| Motion and orientation | Motor-control module and MPU6050-related code |
| Local interface | Keyboard module and I²C LCD support |
| PCB design | KiCad schematic and board files |
| Mechanical reference | STEP model of the robot |

The firmware contains multiple movement and opponent-search routines. Their behavior is hardware-dependent; review the sensor arrangement and motor wiring before deploying a modified build.

## Getting started

Install [PlatformIO](https://platformio.org/) using VS Code or its command-line interface, then open the directory `AML Sumo Robot Code - PlatformIO Project` as a PlatformIO project.

To compile the ATmega2560 firmware from the repository root:

```sh
cd "AML Sumo Robot Code - PlatformIO Project"
pio run -e ATmega2560
```

To upload to a connected, correctly configured target:

```sh
pio run -e ATmega2560 -t upload
```

Uploading requires the appropriate board, serial port, connections, and motor safety precautions. The repository documents a competition-specific hardware build rather than a universal ready-to-run kit.

## Repository guide

- [PlatformIO firmware](AML%20Sumo%20Robot%20Code%20-%20PlatformIO%20Project/) — `src/` contains the main robot behavior and peripheral modules; `platformio.ini` defines the build.
- [KiCad PCB](AML%20Sumo%20Robot%20PCB%20-%20Kicad%20Project/) — board design, schematic, and KiCad project files.
- [Design documents](Document/) — connection reference, schematic export, and planning materials.
- [Mechanical STEP model](PKA_AML_SumoRobot.STEP) — robot assembly reference.

## Scope and reuse

This repository records a physical robotics project. Sensor placement, tuning, pin mapping, and mechanical tolerances depend on the original hardware. It is useful as a technical reference for robot-sumo design and embedded-control experiments.

No repository-wide license is currently declared. Please verify the rights and licenses of included source code, libraries, and design assets before redistribution.
