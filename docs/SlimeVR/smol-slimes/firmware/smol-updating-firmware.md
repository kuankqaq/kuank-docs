# Smol 固件更新


## 所需工具

如果您使用预编译固件，只需要以下工具：
* <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop">nRF Connect for Desktop</a>（编程器）仅用于刷写 Nordic 或 eByte 接收器
* <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop">nRF Connect for Desktop</a>（串行终端）用于向您的接收器/追踪器发送命令，[查看替代方案](smol-pairing-and-calibration.md#accessing-the-serial-console)
* 或 [SmolSlimeConfigurator](SmolSlimeConfigurator.md)，一款适用于您的 Smol Slimes 的多合一编程和配置工具。
* <a href="https://slimevr.dev/download">SlimeVR Server</a>
    * 0.13.2 或更高版本

## 步骤

有关刷写新追踪器和接收器的信息，请查看[刷写固件指南](/smol-slimes/firmware/smol-flashing-firmware.md)。

1. 从[预编译固件](/smol-slimes/firmware/smol-pre-compiled-firmware.md)下载最新的固件版本。
2. 通过 USB 将追踪器连接到计算机，并确保其已开机。
3. 在终端中运行 `dfu` 命令。
4. 您的追踪器将显示为一个名为 `SLIMENRFTRK` 或 `NICENANO` 等的 USB 驱动器（取决于您的追踪器硬件）。
5. 将 UF2 固件文件复制到您的追踪器。
6. 如果更新后追踪器未配对，请参阅[添加更多追踪器](/smol-slimes/firmware/smol-pairing-and-calibration.html#adding-more-trackers)。

!!! info
    复制固件后出现 Windows 错误是常见情况，并**不**表示失败。如果不确定，请在终端中检查提交版本。

!!! warning
    请务必刷写正确的固件版本！不正确的固件可能导致追踪器无响应。

---

*由 Shine Bright ✨、[Depact](https://github.com/Depact) 和 [Seneral](https://github.com/Seneral) 创建。由 [Brisfknibis](https://github.com/brisfknibis) 编辑。*
