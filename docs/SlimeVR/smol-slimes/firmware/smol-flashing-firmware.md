# Smol 刷写引导加载程序和固件

## 目录

* TOC
{:toc}

## 使用 Adafruit UF2 引导加载程序刷写板卡（ProMicro / XIAO）

### 刷写引导加载程序
1. 对于 ProMicro，下载 <a href="https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimenrf_promicro_bootloader-0.9.2-SlimeVR.7_nosd.uf2" target="_blank">update-slimenrf_promicro_bootloader-0.9.2-SlimeVR.7_nosd.uf2</a>。对于 XIAO，下载 <a href="https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimenrf_xiao_sense_bootloader-0.9.2-SlimeVR.7_nosd.uf2" target="_blank">update-slimenrf_xiao_sense_bootloader-0.9.2-SlimeVR.7_nosd.uf2</a>。
1. 使用 USB 数据线将设备连接到计算机。
1. 新设备且无引导加载程序时，设备通常应初始启动进入 DFU 模式。LED 应渐亮渐灭。
1. 如果设备的 LED 没有渐亮渐灭，在 0.5 秒内快速按两次复位按钮（或短暂短接 RST 和 GND 引脚）。如果设备已存在 SlimeNRF 固件，则复位四次。
1. 导航到您的下载文件夹并复制 UF2 文件。
1. 从"此电脑"导航到大容量存储驱动器（例如 NICENANO/XIAO-SENSE）。
1. 将文件粘贴到那里，窗口应关闭，设备将重新启动。

!!! note
    在刷写固件之前，请更新您的 ProMicro 和 XIAO 板上的引导加载程序；否则存在使设备变砖的重大风险。eByte 和 Nordic 接收器不在此类别中。

### 使用 UF2 刷写固件
1. 使用 USB 数据线将设备连接到计算机。
1. 新设备且无引导加载程序时，设备通常应初始启动进入 DFU 模式。LED 应渐亮渐灭。
1. 如果设备的 LED 没有渐亮渐灭，在 0.5 秒内快速按两次复位按钮（或短暂短接 RST 和 GND 引脚）。如果设备已存在 SlimeNRF 固件，则复位四次。
1. 获取固件：
   1. 对于本地构建，导航到本地的接收器或追踪器仓库，然后转到 ```build\REPOSITORY_NAME\zephyr\``` 并复制 "zephyr.uf2" 文件。
   1. 或者，使用[预编译固件](./smol-pre-compiled-firmware.md)。
1. 从"此电脑"导航到大容量存储驱动器（例如 NICENANO/XIAO-SENSE）。
1. 将文件粘贴到那里，窗口应关闭，设备将重新启动。

### 使用 adafruit-nrfutil 刷写固件
这使用引导加载程序的串行协议通过命令行工具进行刷写。<br>
请参阅 <a href="https://github.com/adafruit/Adafruit_nRF52_nrfutil">Adafruit nRF52 nrfutil Github 仓库</a>了解安装和使用说明。<br>
推荐：使用 Python venv 来安装 adafruit-nrfutil Python 工具。

## 使用 SoftDevice/Nordic 引导加载程序刷写接收器（eByte/Nordic/Holyiot）

此引导加载程序将显示为 "Open DFU Bootloader" by Nordic Semiconductor。目前，在这些设备上刷写固件的唯一已确认方法是通过 <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop">nRF Connect for Desktop</a>，但使用 <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Util">nRF Util</a> 也应该可行（但更复杂且实际上等效）。<br>
注意：安装 Segger J-Link 对此引导加载程序不是必需的。<br>
注意：在 Linux 上，nRF Connect for Desktop 将 nodeJS 工具安装到 `~/.nrfconnect-apps/`，nRF Util 将二进制工具安装到 `~/.nrfutil/`。

### 使用 nRF Connect for Desktop 刷写
1. 在 nRF Connect 中打开 "Programmer"。
1. 使用以下任一方法将设备置于 DFU 模式：
    1. 按下复位按钮——LED 应开始渐亮渐灭，表示设备处于 DFU 模式。对于 eByte 接收器，这是右侧按钮。对于 Nordic 接收器，这是侧面按钮（不是圆形白色按钮）。
    2. 对于 HolyIOT-21017 接收器，将附带的磁铁（来自 USB 端口）靠近 LED 区域。红色 LED 应开始渐亮渐灭。
    3. 对于已刷写 SlimeNRF 固件的接收器，在 nRF Connect 中打开串行终端并输入 ```dfu```。（这仅适用于部分 Open DFU Bootloader 设备）
2. 在左上角，选择您的设备。
3. 点击 "Add File"。
4. 选择您要刷写的固件（.hex）：
    1. 对于本地构建，导航到您的本地接收器仓库，然后选择位于 ```build\REPOSITORY_NAME\zephyr\zephyr.hex``` 的文件。
    2. 或者，使用[预编译固件](./smol-pre-compiled-firmware.md)。
5. 点击 "Write" 按钮。如果 udev 错误阻止写入，请遵循[此指南](https://docs.platformio.org/en/latest/core/installation/udev-rules.html)；您可能需要使用提供的替代方法。

### 使用 nRF Util 刷写
尚未记录。相关文档：
- <a href="https://docs.nordicsemi.com/bundle/nrfutil/page/nrfutil-device/guides/programming.html">device 命令文档</a>
- <a href="https://docs.nordicsemi.com/bundle/nrfutil/page/guides-nrf5sdk/dfu_generating_packages.html">nrf5sdk 包构建指南</a>

*由 Shine Bright ✨、[Depact](https://github.com/Depact)、[Seneral](https://github.com/Seneral) 和 [Kresny](https://github.com/Krzeszny) 创建*
