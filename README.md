# RoboMotor

![Project cover](./Image/cover.jpg)

**English** | [中文版](./README_CN.md)

**RoboMotor** is an open-source FOC motor driver project. It provides integrated hardware designs and control algorithms for robotics applications.

## Key Features

- **Hardware Specs**: 4-to-6 layer PCBs designed for 20A-40A continuous current at 24V.
- **Control Algorithm**: Field-Oriented Control (FOC) with current, speed, and position loops.
- **Validation**: Designs tested in RoboMaster environments.

## Hardware

Designed with **KiCad 8**.
For detailed specifications, schematics, and measured performance, please visit the [Hardware](./Hardware/README.md) directory or click on a specific project below.

| Project Name | Target Motor | Key Specs | Core |
| :--- | :--- | :--- | :--- |
| [**RoboMotor-DJI-M3508**](./Hardware/RoboMotor-DJI-M3508/) | [DJI M3508](https://www.robomaster.com/en-US/products/components/general/M3508) | **24V 20A**, 6-Layer, Sin/Cos Encoder | STSPIN32G4 |
| [**RoboMotor-GIM6010-V2**](./Hardware/RoboMotor-GIM6010-V2/) | [GIM6010-8](https://steadywin-motor.com/products/built-in-star-gear-motor-motor-robot-joint-driver-actuator-controller-motor) | **24V 40A**, Dual Encoder Support | STSPIN32G4 |
| [**RoboMotor-GIM6010-V2-Encoder**](./Hardware/RoboMotor-GIM6010-V2-Encoder/) | GIM6010-8 | Magnetic Output Encoder PCB | MA730 |
| [**RoboMotor-GIM6010**](./Hardware/RoboMotor-GIM6010/) | GIM6010-8 | *Legacy Reference Design* | STM32G431 + FD6288 |

## Software

The FOC control algorithm is developed for the **STM32G4** series.

### Features
- **FOC Implementation**: Sensor-based Field-Oriented Control with Flux/Torque decoupling and BEMF feedforward compensation.
- **Control Loops**: 17Khz inner Current loop + outer 4Khz Speed loop + 1Khz Position loop.
- **Connectivity**:
  - **CAN Bus**: Compatible with DJI RoboMaster protocols (M3508/C620).
  - **Custom Protocol**: Extended commands for parameter tuning and telemetry.
- **Additional Functions**:
  - **Auto-Calibration**: Routines for encoder offset and motor parameter identification.
  - **Safety Mechanisms**: Error handling (Over-current, Over/under voltage, Over-temp) with auto-recovery modes.
  - **Feedback Support**: Support for SPI magnetic encoders and analog inputs.

*Find the source code and documentation in the `Software/` directory.*

## License

This project is released under the MIT License.  
See [LICENSE](./LICENSE) for details.


