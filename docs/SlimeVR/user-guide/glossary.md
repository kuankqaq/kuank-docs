# SlimeVR 术语表

!!! warning
    本页提供的定义仅与本文档和 SlimeVR 中的使用相关。相对于其他非 SlimeVR 项目，这些定义可能不准确或缺乏信息。

## 目录

- TOC
  {:toc}

## SlimeVR 服务端

用于接收、处理和输出追踪数据的主要 SlimeVR 应用程序。此应用程序使用 Java 在本地运行，并通过 Websocket 连接到 [SlimeVR GUI](#slimevr-gui) 以提供可视化界面。

### 同义词 {#slimevr-server-synonyms}

- SlimeVR（根据上下文而定）
- SlimeVR 应用
- SlimeVR 软件
- SlimeVR 程序

### 相关术语 {#slimevr-server-related}

- [SlimeVR GUI](#slimevr-gui)
- [SteamVR 驱动程序](#steamvr-driver)

## SlimeVR GUI

[SlimeVR 服务端](#slimevr-server)的可视化界面。此 GUI 作为 webview 运行，并通过 Websocket 连接到 [SlimeVR 服务端](#slimevr-server)。

### 相关术语 {#slimevr-gui-related}

- [SlimeVR 服务端](#slimevr-server)

## SteamVR 驱动程序

SlimeVR 的 SteamVR 驱动程序，将 [VR 头显](#vr-headset)的位置和旋转数据发送到 [SlimeVR 服务端](#slimevr-server)，从 [SlimeVR 服务端](#slimevr-server)接收追踪数据，并使用接收到的追踪数据在 SteamVR 中模拟 Vive 追踪器。

### 同义词 {#steamvr-driver-synonyms}

- SlimeVR 驱动程序

### 相关术语 {#steamvr-driver-related}

- [SlimeVR 服务端](#slimevr-server)

## Feeder 应用

Feeder 应用是一个程序，它连接到 SteamVR 并将来自外部源的追踪器数据转发到 [SlimeVR 服务端](#slimevr-server)。转发的追踪器通常是 VR 控制器、Vive 追踪器或 Tundra 追踪器。

一个常见的误解是 feeder 应用也会转发 [VR 头显](#vr-headset)的追踪数据，但实际上这是由 [SteamVR 驱动程序](#steamvr-driver)完成的。

### 同义词 {#feeder-app-synonyms}

- SlimeVR Feeder
- Feeder

### 相关术语 {#feeder-app-related}

- [SlimeVR 服务端](#slimevr-server)

## 漂移

通常用于描述基于 [IMU](#imu) 的追踪器由于误差随时间累积而经历的追踪精度下降。高漂移的追踪器在 20 分钟内会经历明显的精度损失。漂移通常也以度/小时来衡量——目前对于现代 SlimeVR 追踪器，1-3 度/小时是可接受的漂移水平。

请注意，漂移指的是追踪精度的*逐渐*损失，是追踪器本身的固有特性。用户不良的[安装方向](#mounting-orientation)和[会话校准](#session-calibration)会导致持续性的追踪不准确。

### 同义词 {#drift-synonyms}
- 追踪精度
- IMU 精度

### 相关术语 {#drift-related}
- 加速度计
- 陀螺仪
- 磁力计
- [IMU](#imu)
- 保持对齐
- [重置时间](#reset-time)

## 会话校准

SlimeVR 服务端中有多个不同的会话校准方式；这些通常被称为"重置"。这些校准形式通常不会保存，需要在每次 SlimeVR 会话期间执行。查看[子术语](#session-calibration-sub-terms)了解会话校准的类型。

### 同义词 {#session-calibration-synonyms}

- 完全重置
- 安装校准
- 脚部安装校准
- 软件校准
- VRChat 校准

### 子术语 {#session-calibration-sub}

- [偏航重置](#yaw-reset)
- [安装校准](#mounting-calibration)

## 完全重置

"完全重置"是一种[会话校准](#session-calibration)，它将追踪器重新定向，使俯仰和横滚轴旋转归零，并使偏航轴旋转与头部追踪器（通常是 [VR 头显](#vr-headset)）相同，本质上"重置"（或"归零"）"完整"方向。这通常是开始使用 SlimeVR 会话时使用的第一个校准。

## 安装校准

安装重置（或安装校准）是[会话校准](#session-calibration)的一部分，允许服务端自动测量追踪器的安装方向。如果用户选择使用自动安装，这通常是开始使用 SlimeVR 会话时使用的第二个校准。使用安装校准时，校准结果将覆盖任何手动设置的[安装方向](#mounting-orientation)。

安装校准通常也与脚部安装校准一起提及，后者允许服务端纠正脚部追踪器的方向。

### 同义词 {#mounting-calibration-synonyms}
- 重置安装
- 自动安装
- 自动安装方向

### 相关术语 {#mounting-calibration-related}

- [安装方向](#mounting-orientation)

## 偏航重置

"偏航重置"是一种[会话校准](#session-calibration)，它将追踪器重新定向，使偏航轴旋转与头部追踪器（通常是 [VR 头显](#vr-headset)）相同。由于这仅校准偏航轴，用户可以处于任何位置，只需追踪器都面向其前进方向且与头部追踪器对齐即可。此校准主要用于在上次偏航重置或[完全重置](#full-reset)后经过一段时间来纠正漂移。

### 同义词 {#yaw-reset-synonyms}

- 快速重置
- 快速校准

## 重置时间

重置时间指的是给定 IMU 累积足够漂移以需要进行[偏航重置](#yaw-reset)的大致时间。这是一种主观衡量，取决于用户对漂移的容忍度。

### 相关术语 {#reset-time-related}
- [偏航重置](#yaw-reset)
- [漂移](#drift)

## 安装方向

安装方向是 SlimeVR 追踪器的一种校正方式。它定义了服务端对追踪器相对于其在身体上的物理安装方式的旋转测量。这可以由服务端自动设置（首选），也可以由用户手动校正（不推荐，因为不准确）。

### 同义词 {#mounting-orientation-synonyms}

- 安装方向
- 手动安装

### 相关术语 {#mounting-orientation-related}

- [安装校准](#mounting-calibration)

## VR 头显

VR 头显是一种头戴式设备，可追踪其位置和旋转，通常为每只眼睛配备显示屏。更多信息，请参阅 <https://wikipedia.org/wiki/Virtual_reality_headset>。

### 同义词 {#vr-headset-synonyms}

- 虚拟现实头显
- HMD
- 头戴式设备
- 头显

## Smol Slime

一种 SlimeVR 追踪器类型，使用 nRF 无线接收器代替 Wi-Fi 连接到服务端。

### 同义词 {#smol-slime-synonyms}
- Smols
- Smol 追踪器

### 相关术语 {#smol-slime-related}
- 大/标准 Slime（基于 Wi-Fi 的 Slime）

## 分线板

一种 PCB 类型，旨在将一个或多个集成电路集成到更大的设备中。分线板通常用于 [IMU](#imu)、充电电路和微控制器等组件。

### 同义词 {#breakout-synonyms}
- 分线
- 外部 PCB

### 相关术语 {#breakout-related}
- 微控制器

## IMU

惯性测量单元的缩写。它是一种集成电路，包含一个或多个用于测量运动的设备。SlimeVR 要求 IMU 集成加速度计和陀螺仪，以测量相对于上次重置的加速度和旋转。由于 IMU 本身没有位置参考，因此其传感器随时间不可避免地会累积误差，这称为[漂移](#drift)。低质量的 IMU 比高质量的 IMU 累积误差更快。

### 相关术语 {#imu-related}
- [漂移](#drift)
- 加速度计
- 陀螺仪
- 磁力计
- [完全重置](#full-reset)
- [安装校准](#mounting-calibration)
- [偏航重置](#yaw-reset)

*由 Amebun 更新和编辑。*
