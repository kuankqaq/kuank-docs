# 上传追踪器固件

推荐将 SlimeVR 固件刷写到追踪器的方法是使用 SlimeVR 内置的 [DIY 固件工具](../user-guide/updating-firmware.md#flashing-via-usb-serial)。

请务必选择正确的：
1. 板类型
2. 主 IMU（不要留为 `IMU_AUTO`）
3. 辅助 IMU（不要留为 `IMU_AUTO`，如果不使用扩展模块请移除）

例如，如果你正在使用 ICM45686 构建 [meowCarriers](https://github.com/Shine-Bright-Meow/meowCarrier) 且不使用扩展模块，则应选择：

1. 板类型：Wemos D1 Mini
2. 主 IMU：`IMU_ICM45686`
3. 辅助 IMU：移除

## 替代方案

如果你需要自定义固件，则需要使用 PlatformIO 编译和刷写。

这在以下情况下可能有用：
1. 超频 MCU
2. 交换主和辅助 IMU 地址
3. 开发新的固件功能

以下页面将引导你完成手动刷写追踪器的过程。本指南假设你已经有可正常工作的完整追踪器，并将使用 PlatformIO 方法。所有截图均基于 Windows 系统。

1. [设置环境](setup-and-install.md)
2. [配置固件](configuring-project.md)
3. [构建和上传固件](upload-firmware.md)
