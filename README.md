# Intelligent Fan System

基于 STM32F103C8T6 的智能风扇系统，支持手动调速、温度自动调速、人体红外检测、倒计时、OLED 显示和蓝牙串口控制。

## 目录

- [`source/IntelligentFanSystem`](source/IntelligentFanSystem)：Keil uVision 工程和全部 C 语言源代码
- [`schematics/原理图.pdf`](schematics/原理图.pdf)：系统电路原理图

## 主要硬件接口

| 模块 | STM32 引脚 |
| --- | --- |
| OLED（I²C） | SCL: PB8，SDA: PB9 |
| TB6612 电机驱动 | PWMA: PA2，AIN1: PA4，AIN2: PA5 |
| DHT11 温湿度传感器 | PA8 |
| 红外人体检测 | PA1 |
| 蓝牙串口 | RX: PA9，TX: PA10 |

## 编译

使用 Keil µVision 打开 `source/IntelligentFanSystem/Project.uvprojx`，选择 `STM32F103C8` 目标后编译下载。工程依赖 Keil 的 STM32F1 Device Family Pack 和 ARMCC 工具链。

## 功能说明

- 手动模式：按键或蓝牙指令选择 0–5 档风速。
- 自动模式：根据 DHT11 温度与设定阈值计算 PWM 风速，并结合红外检测启停。
- OLED 显示当前温度、湿度、模式、档位/阈值、速度和倒计时。
