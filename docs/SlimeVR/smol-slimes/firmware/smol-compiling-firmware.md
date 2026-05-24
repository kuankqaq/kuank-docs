# Smol 编译固件

`dmonish warning
如果[默认引脚的预编译固件](./smol-pre-compiled-firmware.md)不满足您的需求，这是编译固件的方法。
`

本页面包含从源代码构建固件的逐步指南，包括所需工具、仓库设置和构建说明。

## 目录

* TOC
{:toc}

## 所需工具
对于有兴趣自行构建固件的人：
* <a href="https://git-scm.com/download/win">Git 客户端</a>
* <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop">nRF Connect for Desktop</a> 及其各种集成工具：
    * Programmer（仅用于刷写 Nordic 和 eByte 接收器）
    * Serial Terminal（用于向您的接收器/追踪器发送命令，[查看替代方案](smol-pairing-and-calibration.md#accessing-the-serial-console)）
    * 注意：对于预定义的板，无需安装 Segger J-Link。
* <a href="https://code.visualstudio.com/download">VS Code</a>（仅用于开发目的）
    * <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-VS-Code">nRF Connect for VS Code by Nordic Semiconductor</a>
        * 从 VS Code 扩展标签页安装。
            * 打开 nRF Connect 标签页。
            * SDK
                * 点击 "Install SDK"。
                * 选择 "nRF Connect SDK"。
                * 选择 "v3.1.0"。
                * 按 "Enter" 键安装在默认位置。
                * 点击 "Install"。
            * 工具链
                * 点击 "Install Toolchain"。
                * 选择 "v3.1.0"。
    * 您也可以在 VS Code 中设置手动构建环境，因为该扩展在某些 Linux 发行版上已知会失败。
* <a href="https://slimevr.dev/download">SlimeVR Server</a>
    * 0.13.2 或更高版本

## 克隆仓库
1. 在开始菜单中输入 `cmd` 打开命令提示符。
1. 导航到您要克隆仓库的目录。（输入 "cd"，后跟空格和目标文件夹或驱动器的完整路径。）
1. 克隆 SlimeNRF 接收器仓库。
`ash
git clone --recurse-submodules https://github.com/SlimeVR/SlimeVR-Tracker-nRF-Receiver.git
`
4. 克隆 SlimeNRF 追踪器仓库。
`ash
git clone --recurse-submodules https://github.com/SlimeVR/SlimeVR-Tracker-nRF.git
`

如果您使用现有的外壳设计，可以选择预构建固件；否则，请自行构建。有关更多详细信息，请参阅 Smol 固件。

**注意：** 建议克隆到不包含空格或 Unicode 字符的文件路径。否则，在构建固件时可能会遇到错误。

## 使用 nRF Connect for VS Code 构建固件
`dmonish important
***ProMicro 构建变体***
**I2C：** 编辑 promicro_uf2.dts 并使用 promicro_uf2/nrf52840/i2c 构建。
**SPI：** 编辑 promicro_uf2.dts 并使用 promicro_uf2/nrf52840/spi 构建。
`

1. 打开其中一个仓库的文件夹。
1. 对 `oards\MANUFACTURER\BOARD_NAME.dts` 进行任何引脚更改或必要的调整。
1. 点击屏幕左侧约一半位置的 nRF Connect 标签页。
1. 在 "Applications" 下，点击 "+ Add build configuration"。
1. 在 SDK 和 Toolchain 下拉菜单中选择 `3.1.0`。
1. 从 "Board Target" 中选择一个预设。
1. 向下滚动并点击 "Build Configuration" 按钮。

**注意：** 对于追踪器，可以在 "Actions" 下的 "nRF Kconfig GUI" 中找到设置，展开 "SlimeNRF" 部分。

### 更改板定义
板定义可在 `\boards\` 中找到，用于覆盖（Zephyr 库中的板），而自定义板位于 `oards\MANUFACTURER\BOARD_NAME.dts`。
1. 导航到板的 .dts 文件。
1. I2C（SCL/SDA）线可以分配到不同的引脚。确保您使用的是 "High Frequency" 引脚，并相应地更改两条线的引脚。
1. SW0 可以通过取消注释（删除 `// `）描述注释下面的行来启用。如果您使用 VS Code，可以选择这些行并按 **Ctrl /**。此外，如有必要，请重新定义 GPIO 引脚。
1. INT（int0-gpios）可以在 Zephyr 用户部分重新定义。
1. 如果您使用的是带有外部时钟或晶振的 IMU（例如 ICM-42688 或 ICM-45686），CLK（clk-gpios）可以取消注释并重新定义。

### 在 Kconfig 中调整设置
1. 导航到 VS Code 的 nRF Connect 标签页。
1. 构建所需的板一次。
1. 左侧导航面板上应显示一个名为 **Actions** 的部分。
1. 在 **Applications** 下选择您已构建的板，然后向下滚动到 **Actions** 部分。
1. 双击 **nRF Kconfig GUI**。
1. 向下滚动到 **SlimeNRF** 部分。
1. 根据需要启用或禁用任何配置，或进行调整。
1. 点击 "Apply" 按钮，然后点击 "Save to File" 按钮。
1. 如果提示选择要保存的文件，请选择 **prj.conf**。
1. 点击 **Actions** 部分中 "Build" 旁边的 "Pristine Build" 按钮。

## 在 Linux 上手动构建固件
仅当您遇到 nRF Connect for VS Code 问题时才推荐此方法，因为您需要手动设置工具链。

### 设置 Python 虚拟环境
使用虚拟环境（venv）将把所有 Zephyr 构建工具（如 west）隔离。<br>
python3 -m venv ~/.venv/nrf52 <br>
source ~/.venv/nrf52/bin/activate（在每次使用或修改时运行此设置。）<br>
pip3 install west

### 设置 nRF Connect SDK 代码
请选择一个合适的文件夹来安装工具链，例如 ~/.toolchain-nrf52。<br>
然后执行：<br>
west init -m https://github.com/nrfconnect/sdk-nrf --mr v3.1.0 nrf52-sdk-3.1.0 <br>
cd nrf52-sdk-3.1.0 <br>
west update（这将下载数十个 Git 仓库；可能需要一些时间。）<br>
pip install -r zephyr/scripts/requirements-base.txt（安装构建所需的其他依赖项。）<br>
west zephyr-export（这将向您的主目录注册必要的 CMake 文件。）<br>
如果您移动此文件夹，只需重新运行最后一个命令。

### 设置 Zephyr SDK
nRF Connect SDK 依赖于 Zephyr SDK，因此请返回您的工具链文件夹（例如 ~/.toolchain-nrf52）进行安装：<br>
wget -q https://github.com/zephyrproject-rtos/sdk-ng/releases/download/v0.17.4/zephyr-sdk-0.17.4_linux-x86_64_minimal.tar.xz <br>
	ar xf zephyr-sdk-0.17.4_linux-x86_64_minimal.tar.xz -C . <br>
cd zephyr-sdk-0.17.4 <br>
./setup.sh -c -t arm-zephyr-eabi（这将向您的主目录注册必要的 CMake 文件。）<br>
如果您移动此文件夹，只需重新运行最后一个命令。

### 手动编译
假设您的工具链安装在 ~/.toolchain-nrf52 中，并且您在固件目录中：
` sh
source ~/.venv/nrf52/bin/activate
source ~/.toolchain-nrf52/nrf52-sdk-3.1.0/zephyr/zephyr-env.sh
west build --board BOARD --build-dir build . -- -DNCS_TOOLCHAIN_VERSION=NONE -DBOARD_ROOT=.
`
将 BOARD 替换为您的特定板（例如 ProMicro 使用 promicro_uf2/nrf52840，接收器使用 
rf52840dongle/nrf52840）。<br>
编译后的固件将位于 PROJECT_DIR/build/PROJECT_DIR/zephyr/zephyr[.hex|.uf2]。

### 使用 VS Code 编译（不带扩展）
假设您的工具链安装在 ~/.toolchain-nrf52 中，请使用以下任务，这些任务应放置在 .vscode/tasks.json 中：
` JSON
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Build",
            "type": "shell",
            "group": "build",
            "command": "source",
            "args": [
                "~/.venv/nrf52/bin/activate", "&&",
                "source", "~/.toolchain-nrf52/nrf52-sdk-3.1.0/zephyr/zephyr-env.sh", "&&",
                "west", "build", "--board", "BOARD", "--build-dir", "build",
                "", "--",
                "-DNCS_TOOLCHAIN_VERSION=NONE", "-DBOARD_ROOT="
            ]
        },
    ]
}
`
将 BOARD 替换为您的特定板（例如 ProMicro 使用 promicro_uf2/nrf52840，接收器使用 
rf52840dongle/nrf52840）。<br>
编译后的固件将位于 PROJECT_DIR/build/PROJECT_DIR/zephyr/zephyr[.hex|.uf2]。

## 协议
`dmonish important
本节提供有关通信协议的高级信息，并非构建您自己的 smol slimes 所必需。
`

<details>
  <summary>HID 协议</summary>

`dmonish warning
HID 协议尚未最终确定，在未来的 SlimeVR Server 版本中可能会发生变化。
`

### 追踪器 -> 服务器
`
b0      |b1      |b2      |b3      |b4      |b5      |b6      |b7      |b8      |b9      |b10     |b11     |b12     |b13     |b14     |b15     |
type    |id      |packet data                                                                                                                  |
0       |id      |proto   |batt    |batt_v  |temp    |brd_id  |mcu_id  |imu_id  |mag_id  |fw_date          |major   |minor   |patch   |rssi    | info
1       |id      |q0               |q1               |q2               |q3               |a0               |a1               |a2               | full precision quat
2       |id      |batt    |batt_v  |temp    |q_buf                              |a0               |a1               |a2               |rssi    | reduced precision quat
3       |id      |svr_stat|status  |resv                                                                                              |rssi    | status
4       |id      |q0               |q1               |q2               |q3               |m0               |m1               |m2               |
255     |id      |addr                                                 |resv                                                                   |
`

### 追踪器 <-> 接收器
`
b0      |b1      |b2      |b3      |b4      |b5      |b6      |b7      |b8      |b9      |b10     |b11     |b12     |b13     |b14     |b15     |
type    |id      |packet data                                                                                                                  |
64      |id      |addr                                                 |resv                                                                   | pairing data from tracker
65      |id      |addr                                                 |addr_rcv                                             |channel |resv    | pairing data to tracker
66      |id      |addr                                                 |time                                                                   | timing data to tracker (why addr?)
67      |id      |addr                                                 |cmd_data                                                               | some command to tracker? (need to be part of timing?)
`

### 追踪器 <-> 服务器
`
b0      |b1      |b2      |b3      |b4      |b5      |b6      |b7      |b8      |b9      |b10     |b11     |b12     |b13     |b14     |b15     |
type    |id      |packet data                                                                                                                  |
128     |id      |addr                                                 |cmd_data                                                               | some command to tracker? (field too large?)
128     |id      |addr                                                 |ack                                                                    | acknowledge?
`

### 接收器 <-> 服务器
`
b0      |b1      |b2      |b3      |b4      |b5      |b6      |b7      |b8      |b9      |b10     |b11     |b12     |b13     |b14     |b15     |
type    |id      |packet data                                                                                                                  |
192     |id      |resv                                                                                                                         | 192+ should be some interaction b/w receiver and server
254     |resv                                                                                                                                  | filler, this packet is ignored by the server
255     |id      |addr                                                 |resv                                                                   | tracker id association
`

</details>

## 故障排除
`dmonish important
请在相应仓库中为任何固件错误或问题提交 GitHub issue。
`

### 检查控制台日志

1. 启动 nRF Connect for Desktop。
1. 在 nRF Connect 中打开 Serial Terminal。
1. 确保您的追踪器已通过线缆连接到计算机。
1. 在左上角，在 Devices 下选择您的追踪器。
1. 点击 "Connect to Port" 按钮。

#### 改进日志记录

- 要更改您看到的日志级别（例如，LOG_DBG 而不是仅 LOG_INF），您可能需要编辑相关模块或文件顶部的 LOG_MODULE_REGISTER 宏，然后重新编译固件。<br>

- 如果您需要在连接到串行控制台之前查看日志，您可能需要在 main.c 的主函数中显式初始化日志后端，添加以下代码片段：
    ` C
    const struct log_backend *backend = log_backend_get_by_name("log_backend_uart");
    log_backend_enable(backend, backend->cb->ctx, CONFIG_LOG_MAX_LEVEL);
    `
    此外，在 main.c 文件的顶部添加以下 include：<br>
    `C
    #include <zephyr/logging/log_ctrl.h>
    `
- 如果您注意到日志在某个点被截断，则可能是缓冲区大小不足。此问题尚未完全解决，因为简单地增加 prj.conf 中的 CONFIG_LOG_BUFFER_SIZE 似乎无效。

#### SWD 调试
* 有关 Raspberry Pi、Raspberry Pi Pico、ST-Link V2 和其他调试器的说明将在未来添加。
**资源：** <a href="https://github.com/joric/nrfmicro/wiki/Bootloader">https://github.com/joric/nrfmicro/wiki/Bootloader</a>

#### J-Link、nRF52/nRF52840 开发套件和 OB-ARM 调试器
1. 安装 J-Link 软件和文档包：<a href="https://www.segger.com/downloads/jlink/#J-LinkSoftwareAndDocumentationPack">https://www.segger.com/downloads/jlink/#J-LinkSoftwareAndDocumentationPack</a>
1. 下载您的设备的引导加载程序 HEX 文件（ProMicro - <a href="https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimenrf_promicro_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex" target="_blank">slimenrf_promicro_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex</a>，XIAO - <a href="https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimenrf_xiao_sense_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex" target="_blank">slimenrf_xiao_sense_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex</a>）
1. 将调试器连接到 SWD IO、CLK 和 GND 引脚。（通过 USB 为设备供电比使用 VDD 引脚更安全）

##### 刷写/修复变砖的引导加载程序
1. 启动 "J-Flash Lite"。
    * **Target Device：** NRF52840_XXAA
    * **Target Interface：** SWD
    * **Speed：** 4000
1. 点击 "OK" 按钮。
1. 点击 "..." 按钮并选择下载的 HEX 文件。
1. 点击 "Program Device" 按钮。

##### RTT/调试
1. 启动 "RTT Viewer"。
    * **Connection to J-Link：** USB
    * **Specify Target Device：** NRF52840_XXAA
    * **Force go on connect：** 已勾选
    * **Target Interface & Speed：** SWD / 4000 kHz
    * **RTT Control Block：** Auto Detect
1. 点击 "OK" 按钮。

#### 推荐硬件/工具
**OB-ARM 调试器：** <a href="https://www.aliexpress.us/item/3256806507382540.html">https://www.aliexpress.us/item/3256806507382540.html</a>

**Pogo Pin 测试夹（1.5mm 间距，4P，单排）：** <a href="https://www.aliexpress.us/item/3256805646654844.html">https://www.aliexpress.us/item/3256805646654844.html</a>

**注意：** 此夹子专为 ProMicro 设计。虽然有更便宜的夹子可用，但它们不能将引脚从 1.5mm 间距转换为适合杜邦线的 2.54mm 间距。

## 链接

### 固件源代码
| 名称 | 链接 |
| ---------------------------- | ----------------------------------------------------------------- |
| SlimeVR Tracker nRF Receiver | [Github](https://github.com/SlimeVR/SlimeVR-Tracker-nRF-Receiver) |
| SlimeVR Tracker nRF          | [Github](https://github.com/SlimeVR/SlimeVR-Tracker-nRF)          |

### 社区固件

| 名称 | 作者 | 描述 | 链接 |
| ----------------- | ---------- | -------------------------------------------------------------------------- | ---------------------------------------------------------- |
| Stacked-SmolSlime | LyallUlric | 主分支的 fork，固件针对堆叠式 ProMicro 追踪器进行了定制。 | [Github](https://github.com/LyallUlric/Stacked-SmolSlime/) |

<hr/>

*由 Shine Bright ✨、[Depact](https://github.com/Depact) 和 [Seneral](https://github.com/Seneral) 创建*
