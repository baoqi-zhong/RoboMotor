# RoboMotor

![Project cover](./Image/cover.jpg)

[English](./README.md) | **中文**

**RoboMotor** 是一个开源 FOC 电机驱动项目，提供完整的硬件设计方案与控制算法。

## 主要特性

- **硬件规格**: 采用 4-6 层 PCB 设计，支持 24V 下 20A-40A 持续电流。
- **控制算法**: 完整的磁场定向控制 (FOC)，包含电流、速度、位置三闭环。
- **验证**: 方案在 RoboMaster 备赛环境中经过验证。

## 硬件设计

项目使用 **KiCad 8** 设计。
详细规格、原理图及测试数据，请访问 [Hardware](./Hardware/README.md) 目录或点击下表中的具体项目链接。

| 项目名称 | 适配电机 | 关键参数 | 主控方案 |
| :--- | :--- | :--- | :--- |
| [**RoboMotor-DJI-M3508**](./Hardware/RoboMotor-DJI-M3508/) | [DJI M3508](https://www.robomaster.com/en-US/products/components/general/M3508) | **24V 20A**, 6层板, 支持 Sin/Cos 编码器 | STSPIN32G4 |
| [**RoboMotor-GIM6010-V2**](./Hardware/RoboMotor-GIM6010-V2/) | [GIM6010-8](https://steadywin-motor.com/products/built-in-star-gear-motor-motor-robot-joint-driver-actuator-controller-motor) | **24V 40A**, 支持双编码器 | STSPIN32G4 |
| [**RoboMotor-GIM6010-V2-Encoder**](./Hardware/RoboMotor-GIM6010-V2-Encoder/) | GIM6010-8 | 输出端磁编码器 PCB | MA730 |
| [**RoboMotor-GIM6010**](./Hardware/RoboMotor-GIM6010/) | GIM6010-8 | *早期参考设计* | STM32G431 + FD6288 |

## 软件方案

核心 FOC 算法针对 **STM32G4** 系列 MCU 优化。

### 功能特点
- **FOC 实现**: 有感 FOC 控制，支持 DQ 轴解耦与反电动势前馈补偿。
- **闭环控制**: 17KHz 高频电流内环 + 4KHz 速度环 + 1KHz 位置环。
- **通信协议**:
  - **CAN 总线**: 兼容 DJI RoboMaster 电机协议 (M3508/C620)。
  - **自定义协议**: 支持编码器, 扭矩电流等数据回传。
- **辅助功能**:
  - **自动校准**: 编码器零点偏置检测与电机参数自动辨识。
  - **安全机制**: 完善的过流、过欠压等保护及自动恢复策略。
  - **传感器支持**: 支持 SPI 磁编码器及模拟量输入。

*源码及相关文档位于 `Software/` 目录。*

## 许可证

本项目基于 MIT License 开源。
详情请见 [LICENSE](./LICENSE)。
