# Smol 配对与校准

本页面包含配对追踪器和接收器、校准传感器以及使用控制台命令进行设置和故障排除的说明。

## 概述

本指南介绍如何配对、校准和更新您的 Smol Slime 追踪器和接收器。您需要使用串口终端程序（如 <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop" target="_blank">nRF Connect</a> 或 <a href="https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html" target="_blank">PuTTY</a>）来运行设置和故障排除命令。

## 所需工具

您需要一个串口终端程序来向追踪器和接收器发送命令。

* **推荐：** 下载并安装 <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop" target="_blank">nRF Connect for Desktop</a>。
  * 在其内部安装串口终端模块。
* **Linux/Mac：**
  * ```
    sudo screen /dev/ttyACMX 115200
    ```
    *（使用 `sudo dmesg` 查找您的端口。）*
* **Windows 替代方案：** <a href="https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html" target="_blank">PuTTY</a>

!!! tip
    想要更易用的应用程序？请查看 [SmolSlimeConfigurator](SmolSlimeConfigurator.md)

## 配对追踪器（首次）

首次刷写固件后，追踪器和接收器会自动进入配对模式。

1. 如果设备未处于配对模式：
   * **接收器：** 运行 `pair`
   * **追踪器：** 按住 **SW0**（功能）按钮 5 秒钟（*或短接 RST/GND 3 次*）
     * 配对模式下 LED 每秒闪烁一次。
2. 在接收器控制台中观察 `esb_event` 输出：
   * ```<inf> esb_event: Added device on id 0 with address 95CB23A0FDF7```
3. 通过 USB 将追踪器连接到计算机。
4. 配对成功后，追踪器的 LED 闪烁四次。
5. 对所有追踪器重复上述步骤。
6. 在接收器上输入 `exit` 退出配对模式。

## 添加更多追踪器

您可以一次将一个追踪器配对到接收器，方法是在接收器上使用 `add` 命令，然后在追踪器上使用 `set` 命令。

1. 在追踪器上运行：`info`
2. 复制其"设备地址"（例如 `95CB23A0FDF7`）。
3. 在您的**接收器**上：`add 95CB23A0FDF7`（将设备地址替换为您自己的）。
4. 从接收器输出中复制配对 ID：
    * ```[00:46:06.485,778] <inf> esb_event: Pair the device with D94BDEF1E442005B```
5. 在您的**追踪器**上：`set D94BDEF1E442005B`
6. 在**追踪器**上确认配对 — 您应该看到：
    * ```[00:30:51.060,028] <inf> esb_event: Paired```
7. 对每个额外的**追踪器**重复所有步骤。

!!! tip
    配对后追踪器 LED 将停止闪烁。通过移动追踪器检查它是否出现在 SlimeVR Server 中，以确认连接。如果没有出现，`reboot` 追踪器和接收器，然后在接收器上 `exit` 配对模式。

## 校准追踪器

### 基本校准

基本校准运行加速度计和陀螺仪零速率偏移。这通常就足够了。有两种方法。校准时，将追踪器平放在表面上并保持静止，直到 LED 指示完成。

- **方法 1：** 按下 **SW0**（功能）按钮两次，然后等待 LED 闪烁四次以确认校准完成。
- **方法 2：** 将追踪器连接到计算机并运行 `calibrate`。

### 六面校准

六面校准在所有六个轴上对齐加速度计。此方法要求您在所有 6 个面上保持追踪器完全静止。

1. 在通电状态下将追踪器连接到计算机。
2. 运行 `6-side` 命令。
3. 按提示将追踪器放在每个面上。控制台将提示您何时旋转，或者您可以观察 LED 成功闪烁。

!!! tip
    执行 `6-side` 命令后，您可以立即拔掉电缆。当提示放置最后一个面时，断开 USB 电缆并将带有 USB 端口的面放在平坦表面上会更方便。

!!! warning
    不正确的 `6-side` 校准可能会使追踪变得更差！校准时请将追踪器稳定地放置在**平坦、稳定**的表面上。

### 磁力计

磁力计校准默认禁用。启用后，它会自动运行 — 无需按钮或命令。将追踪器平放在表面上，缓慢旋转 360°，依次完成六个面。

当您将追踪器平放在每个面上时，LED 会闪烁，当准备好保存时会持续闪烁。

!!! warning
    磁力计可以改善追踪效果；但是，在存在强磁干扰的环境（如金属桌子或 PC 附近）中，性能可能会变差。

## 故障排除

### Linux：SlimeVR Server 无法检测到接收器

对于 Linux 系统，可能需要创建一个 udev 规则，以便 SlimeVR Server 将接收器检测为 HID 设备。

创建规则文件：
```bash
touch /etc/udev/rules.d/99-hid-dongle.rules
```
将以下规则添加到文件中：
```bash
sudo tee /etc/udev/rules.d/99-hid-dongle.rules > /dev/null <<'EOF'
SUBSYSTEM=="usb", ATTR{idVendor}=="1209", ATTR{idProduct}=="7690", MODE="0666"
KERNEL=="hidraw*", SUBSYSTEM=="hidraw", ATTRS{idVendor}=="1209", ATTRS{idProduct}=="7690", MODE="0666"
EOF
```
确认规则已生效：
```bash
cat /etc/udev/rules.d/99-hid-dongle.rules
```
**注意：** 您可能需要根据接收器的实际情况更新 `idVendor` 和 `idProduct` 值。使用 `lsusb` 查找正确的 ID。

### 追踪器已配对但未出现在 SlimeVR Server 中

* 在接收器上：`exit`。
* 重启追踪器：`reboot` 或按下 **SW0** 按钮。
* 重启接收器：`reboot`。
* 确保在追踪器上检测到 IMU：`info`。
  * 正常：`IMU: ICM-45686`
  * 无法检测：`IMU: None`

### 追踪器反复输出串口警告 `<wrn> sensor: No packets in buffer` 和 `<wrn> sensor: Sensor interrupt timeout`

<img src="../assets/img/smol-pairing-and-calibration/Sensor interrupt timeout.png" loading="lazy" class="big-size-image"/>

如果追踪器反复输出这些警告：
```
<wrn> sensor: No packets in buffer
<wrn> sensor: Sensor interrupt timeout
```

**初步检查：**
- 使用专用的重启按钮（如果有）重启追踪器，或短暂短接 RST 和 GND 引脚。

**诊断步骤：**
- 运行 `info` 命令以确认 IMU 检测。

**如果检测到 IMU，解决方案：**
- 检查 `INT1` 引脚是否焊接良好。
  请参阅原理图：<a href="../hardware/smol-tracker.md#schematics">Smol Tracker</a>

## 参考

### 状态码

状态码由一个或多个状态值（相加）组成，如下所列：

| 代码 | 含义                           |
| ---- | ------------------------------ |
| 1    | SYS_STATUS_SENSOR_ERROR        |
| 2    | SYS_STATUS_CONNECTION_ERROR    |
| 4    | SYS_STATUS_SYSTEM_ERROR        |
| 8    | SYS_STATUS_USB_CONNECTED       |
| 16   | SYS_STATUS_PLUGGED             |
| 32   | SYS_STATUS_CALIBRATION_RUNNING |
| 64   | SYS_STATUS_BUTTON_PRESSED      |

---

*由 Shine Bright ✨、[Depact](https://github.com/Depact) 和 [Seneral](https://github.com/Seneral) 创建。由 [Brisfknibis](https://github.com/brisfknibis) 编辑。*
