# 常见问题

本页面旨在列出并提供常见问题的解决方案。如果此处没有回答你的问题，或给定的修复方法没有帮助，请随时在 [SlimeVR Discord](https://discord.gg/slimevr) 的 [#support-forum](https://discord.com/channels/817184208525983775/1025104406393405491) 中提问。寻求帮助时，请务必说明你在此处尝试过的所有步骤。请记住，某些解决方案可能不适用于你的 SlimeVR 追踪器，尤其是 DIY 或从第三方卖家购买的追踪器。

* TOC
{:toc}

## 网络配置文件当前设置为公共

如果你的 Windows 网络设置设置为"公用网络"，可能会导致 SlimeVR 追踪器连接到 PC 时出现问题。
可按以下步骤更改：

**Windows 10**

通过 Windows 设置 > 网络和 Internet > 属性打开网络设置。
将"网络配置文件类型"设置切换为"专用网络"。

![network3](assets/img/network_private_3.png)
![network4](assets/img/network_private_4.png)
![network5](assets/img/network_private_5.png)

**Windows 11**

通过 Windows 设置 > 网络和 Internet 打开网络设置。根据你的 PC 连接方式，你可以点击"属性"或"以太网/WiFi"。
然后，将"网络配置文件类型"设置切换为"专用网络"。

![network1](assets/img/network_private_1.png)
![network2](assets/img/network_private_2.png)

## SlimeVR Feeder 应用未连接

确保 SlimeVR 和 SteamVR 都在运行，并且在启动叠加应用中启用了 SlimeVR Feeder 应用。按照下面的指南启用它。

![Enable Feeder App](assets/img/Spazzwan-enable-feeder-app.webp)

如果应用未在 SteamVR 中显示，你可能需要以修复模式再次运行 SlimeVR 安装程序。在继续之前，确保勾选了"SlimeVR Feeder App"。

![Repair Feeder App](assets/img/Common-issues-repair-feeder-app.webp)

## Feeder 应用窗口打开后立即关闭

这是较新版本的预期行为——Feeder 应用在窗口自动关闭后继续在后台运行。

## SlimeVR 服务端无法启动

- 如果错误与端口相关，确保所有其他 SlimeVR 服务端实例已关闭。如果问题仍然存在，请重启 PC。
- 这也可能是由于未安装 Java 或 Java 安装问题引起的。再次运行[安装服务端页面](../server/initial-setup.md#install-the-latest-slimevr-installer)中链接的安装程序应能解决此问题。

## SlimeVR 窗口卡在小窗口状态

使用[安装程序](https://slimevr.dev/download)更新你的 SlimeVR 服务端。

## SlimeVR GUI 立即崩溃 / "panicked at ... WebView2Error" / WebView2 缺失

可能是你没有安装所需的 WebView2 组件，你可以从 <https://developer.microsoft.com/en-us/microsoft-edge/webview2/consumer/> 下载 WebView2 安装程序。为确保 WebView2 正确安装，请以管理员身份运行 WebView2 安装程序（右键单击，然后选择"以管理员身份运行"），并确保安装程序从 C: 驱动器运行（例如 `C:\MicrosoftEdgeWebview2Setup.exe`），并从那里运行。

## SlimeVR GUI 频繁超时 / 反复显示"与服务器连接丢失。正在尝试重新连接..."

- 如果你的 SlimeVR GUI 反复从 SlimeVR 服务端超时（检查日志），你可以通过在管理员控制台中运行以下命令来修复：`netsh int tcp set supplemental internet congestionprovider=default`。这是由修改版操作系统常用的非默认 Windows 网络配置引起的。
- 或者，尝试以修复模式运行 SlimeVR 安装程序。

## Wi-Fi 设置窗口输出 ERROR

尝试重置追踪器，这可能会立即解决问题。尝试将追踪器连接到不同的 USB 端口，和/或尝试不同的 USB 线缆。如果问题仍然存在，你的 COM 端口可能被占用，可以通过在 VSCode 中进行固件更新过程来测试（因为它提供更详细的错误信息）。如果是这种情况，请关闭可能占用端口的任何应用程序（VSCode 和 Cura 通常是原因）。

## Wi-Fi 设置窗口仅输出符号而无其他内容

有两个常见原因需要检查：

- 确保你已安装正确的驱动程序。
- 检查你的 PIO 固件上传是否成功。如果你在 VSCode 中打开了多个固件版本，则需要将正确版本设置为默认上传。

## 追踪器无法连接到 Wi-Fi

导致此错误的两个常见问题是：

- 确保你连接到的是 2.4GHz 网络，不支持 5GHz 网络。
- 检查你的 SSID 是否包含特殊字符。目前 SlimeVR 仅支持包含字母数字字符的网络 SSID。
- 确保你使用 Wi-Fi 信道 1-11。避免使用信道 12-14，因为可能发生连接问题。
- 确保未使用 WPA3 Wi-Fi 安全协议，SlimeVR 追踪器不支持此安全协议。建议使用 SlimeVR 完全支持的 WPA2。
- 尝试重启路由器，看是否能解决问题。
- 使用 Wi-Fi 7 路由器时，尝试禁用 MLO 或将模式从"性能"切换为"兼容性"模式（有时称为"最大互操作性"模式）。

如果以上都正确，你可以检查网关的已连接设备列表，查看所有追踪器是否都已连接。如果追踪器在使用硬编码 Wi-Fi 信息的相同固件上传后仍未连接，还有两个额外步骤可以检查：

- 检查你的 Wi-Fi 是否已达到最大允许连接数。你可以通过断开其他设备然后尝试重新连接追踪器来测试。
- 如果你在 `platformio.ini` 中硬编码了 Wi-Fi 设置，尝试通过 USB 连接追踪器并[推送新的 Wi-Fi 信息](../server/connecting-trackers.md#connect-trackers)。这可能会修复连接问题，或为你提供连接失败的额外信息。

## 追踪器已连接到 Wi-Fi 但找不到服务端

检查你是否运行了两个 SlimeVR 服务端实例，因为只有一个会显示追踪器已连接。

如果只有一个服务端在运行，这很可能是防火墙问题，请进入 SlimeVR 服务端文件夹并以管理员身份运行 `firewall.bat`，以向 Windows Defender 防火墙添加防火墙规则。

如果仍有问题，请尝试将 SlimeVR 服务端手动添加到防火墙。

1. 前往**设置** > **网络和 Internet**，然后点击文本链接**Windows 防火墙**（你可能需要向下滚动）。
1. 在防火墙窗口中，点击**允许应用通过防火墙**链接。
1. 点击**允许其他应用...**按钮，然后在打开的**添加应用**窗口中点击**浏览...**。如果**允许的应用**窗口中的选项呈灰色，请点击**更改设置**按钮以允许更改。
1. 在**文件名**文本框中，输入 `*.*` 并按回车，然后导航到 SlimeVR 服务端文件夹中的 `slimevr.jar` 并选择它（如果在此文件夹中看不到文件，请尝试再次输入 `*.*` 并按回车以显示所有文件）。
1. 点击**添加**按钮将文件添加到防火墙设置。
1. 最后，确保在**允许的应用**窗口中同时勾选了公用和专用复选框，然后点击**确定**保存更改。

如果添加 SlimeVR 到防火墙无效，你可以尝试以下步骤进一步诊断问题：

1. 确保计算机的以太网/Wi-Fi 连接设置为专用。
1. 确保在活动的网络接口上启用了网络发现。
1. 禁用任何 VPN 软件或支持 VPN 的硬件。
1. 确保你的追踪器未连接到访客 Wi-Fi 网络。
1. 确保 Wi-Fi 网络**未**启用 AP 隔离。
1. 删除 SlimeVR 配置：关闭 SlimeVR 并删除 `%AppData%\dev.slimevr.SlimeVR` 下的配置文件夹。
1. 如果你在另一台设备上安装并运行 SlimeVR 服务端然后关闭，追踪器应重新连接到之前使用的服务端。
1. 临时禁用 Windows Defender 防火墙或任何其他防病毒软件，以测试追踪器是否能连接。
   - 如果仅在禁用 Windows Defender 防火墙时追踪器才出现在 SlimeVR 中，则说明你的防火墙有问题。
1. 尝试从计算机 ping 追踪器，看是否可达。打开命令提示符 (CMD) 并运行命令 `ping <IP>`，其中 `<IP>` 是你的追踪器 IP（例如 `ping 192.168.0.1`）。你可以在 SlimeVR GUI 的"设置"选项卡下的"串行控制台"中查找追踪器 IP。
   - 如果命令输出类似 `来自 192.168.XXX.XXX 的回复：无法访问目标主机。`，则你很可能遇到路由器或防火墙的问题。
   - 如果命令输出类似 `来自 192.168.XXX.XXX 的回复：字节=32 时间<1ms TTL=63`，则你很可能遇到网络适配器或网络设置的问题。你可能需要在路由器上启用广播数据包（或类似功能），因为 SlimeVR 追踪器广播到 `255.255.255.255` 以发现你的 SlimeVR 服务端。
1. 尝试从计算机或手机托管 Wi-Fi 热点，并将追踪器连接到该热点，看它们是否会出现在 SlimeVR 中。
   - 如果追踪器未出现在 SlimeVR 中，则你很可能遇到追踪器或计算机的问题。值得尝试按照第一步禁用 Windows Defender 防火墙，但改用此 Wi-Fi 热点。
   - 如果追踪器出现在 SlimeVR 中，则你很可能遇到路由器或连接路由器的网络适配器的问题。
1. 重新刷写固件到旧版本。

如果以上步骤均无效，你可以在[本页顶部](#常见问题)找到获取进一步帮助的信息。

## 追踪器已连接到 SlimeVR 服务端但未显示

这通常是 IMU 问题的结果。插入你的 Wemos D1 Mini，并通过 SlimeVR 服务端中设置下的串行控制台检查。你可能会看到类似以下错误：

```c
[ERR] I2C: Can't find I2C device on provided addresses, scanning for all I2C devices and returning
[ERR] I2C: No I2C devices found
[ERR] I2C: Can't find I2C device on provided addresses, scanning for all I2C devices and returning
[DBG] I2C (@ D2(4) : D1(5)): I2C device found at address 0x68  !
[ERROR] [ErroneousSensor:0] IMU of type MPU6500 failed to initialize
```

IMU 错误的最常见原因如下：

1. 你意外设置了错误的 IMU（例如设置为 MPU6050，而实际为 BNO085）
1. 你意外选择了错误的板型（例如设置为 BOARD_SLIMEVR，而应为 BOARD_WEMOSD1MINI）
1. 接线错误（例如意外交换了 D1/D2 和 SDA/SCL）
1. 焊接问题（例如焊锡不足、冷焊或 SDA 与 SCL 之间桥接）
1. 你使用了面包板（未焊接连接时，IMU 通常无法与微控制器通信）
1. IMU 本身有问题（例如焊接时烧坏引脚，或芯片直接坏掉）

## 追踪器已连接到 SlimeVR 服务端但未在 Steam 上显示

- 确保你已通过[安装程序](https://slimevr.dev/download)安装 SlimeVR，以获得正确的 SteamVR 驱动程序。
- 确保在 SteamVR 设置 > 启动/关闭 > 管理附加组件中启用了 SlimeVR 插件。
- 确保你在 [SlimeVR 设置中启用了 SteamVR 追踪器](../server/configuring-trackers.md#configuring-how-many-virtual-trackers-you-need)。

## 我的追踪器持续闪烁

这是预期行为，闪烁次数表示追踪器的当前状态。请查看[设置页面顶部的更多信息](../server-setup/initial-setup.md#test-your-trackers)。

## 我的辅助追踪器不工作
- 确保在连接辅助追踪器之前已关闭主追踪器电源。
- 为确保正确设置辅助追踪器，你需要在上传到主追踪器固件的 `defines.h` 中指定它。请查看[配置 SlimeVR 固件页面中关于定义引脚的部分底部](../firmware/configuring-project.md#define-pins-of-the-selected-board)。或者，确保你已正确将 VCC 焊接到辅助追踪器 IMU 上的 AD0。

## 传感器已重置错误

检查你的 INT 线，可能存在连接不良或将其连接到了闪存引脚。如果你在面包板上构建追踪器，连接可能不够牢固，导致此错误。

## 追踪器漂移超出预期

- 确保追踪器在通电时放置在坚固、无振动的表面上。传感器需要在稳定的环境中校准 10-20 秒。如果你的追踪器使用除 BNO085 和 ICM-45686 之外的 IMU，你可能需要执行额外的 [IMU 校准](../server/imu-calibration.md)。
- 此外，使用 15 分钟或更长时间后，取下追踪器并平放 10-20 秒后再戴上。这确保 IMU 适应你的体温。

## 脚踝和脚部追踪器显示为一个追踪器
这是正常的。SlimeVR 将脚踝追踪器的位置与脚部追踪器的旋转相结合——这意味着 SteamVR 只报告一个脚部追踪器。

## 我的追踪器在 SteamVR 中绑定到错误的身体部位
如果在 SteamVR 中发生此问题，请确保在 SlimeVR 中将追踪器分配到正确的身体部位。不要在 SteamVR 中调整分配。

## 在 VRChat 中移动一个追踪器会移动其他身体部位
- 确保 VRChat 中的 IK 校准范围设置为 0.2。
- 确保在 VRChat 中禁用了旧版校准和旧版 IK。

## 移动时追踪器朝错误方向移动

- 使用自动安装校准代替手动。
- 确保服务端中追踪器的安装方向与其在身体上的实际位置一致（对于某些设置，你可能需要提供不同的方向）。
**仅限 DIY：** 你可能在 `defines.h` 文件中指定了错误的 `IMU_ROTATION` 值。请注意哪些追踪器出现问题，并参考[配置 SlimeVR 固件页面](../firmware/configuring-project.md#adjust-imu-board-rotation)以获取正确的板旋转角度。
如果只差几度，请将追踪器向内或向外稍微调整，然后重新进行自动安装校准。

## 我的脚陷入地板 / 我经常滑行

这可能是由于你的物理或骨骼长度设置问题。尝试：

- 确保在 SlimeVR 设置 > 追踪设置中启用了"滑冰校正"和"地板裁剪"（目前不适用于 Quest 独立版本）。
- 重新执行自动校准。
- 调整实际的追踪器安装位置。

## 我的脚部不正确/移动不正确
- 确保在 SlimeVR 服务端中安装校准后完成了脚部安装重置。
- 尝试改变脚部的角度；根据你的体型，更高或更低的角度可能效果更好。在脚部校准期间，不应向任何一侧倾斜。

## 我的角色漂浮在地面上方

- 通过重新绘制边界来确保地平面正确。如果在 Quest 或其他独立头显上，请清除边界历史记录。
- 确保 SlimeVR 和 VRChat 中的身高设置均为你的实际身高。
- 这也可能是由特定角色的罕见问题引起的，尝试切换到其他角色并在 VRChat 中重新校准。
- 如果你使用 Quest 头显，请在头显设置中关闭"使用躺卧姿势"（或类似选项）。这可能导致漂浮和下沉问题。

## 我的腿无法弯曲

- 确保你的大腿追踪器位于膝盖上方并分配为"大腿"追踪器，脚踝追踪器位于脚踝上方并分配为"脚踝"追踪器。
- 确保你的脚踝追踪器在脚踝上，而不是在脚上。

## 坐下时我的腿交叉

- 确保在安装校准时，双脚之间的距离不小于 10cm。
- 尝试将大腿追踪器向外以一定角度安装。
- 根据你的体型，尝试将大腿追踪器戴在大腿更高或更低的位置。
- 在身体比例菜单中重置身体比例和身高。
- 使用偏航重置来纠正腿部交叉：[为重置分配按键绑定](../server/setting-reset-bindings.md)。

## 我的一条腿比另一条高

稍微移动你的大腿追踪器；尝试其他安装位置和方向。

## AutoBone / 自动身体比例校准不起作用

如果 AutoBone 无法正常工作，你可以在[身体比例配置页面的"常见问题 / 调试"部分](../server/body-config.md#common-issues--debugging)找到常见问题和调试信息列表。

## 未检测到串行设备 / "正在寻找追踪器" / "与串行连接丢失，正在重新连接..."

如果你在"连接追踪器"步骤中无法检测到追踪器、在串行控制台中未显示、在网页固件工具中未显示或在 VSCode 中未检测到，请确保检查以下内容：
- 如果你使用官方追踪器，确保它们已打开并且蓝灯闪烁。如果蓝灯未闪烁，可能存在其他问题。
  - 对于大多数 DIY 追踪器，它们应处于**关闭**状态作为安全预防措施，因为 ESP 应通过 USB 直接供电。
- 如果你使用 DIY 追踪器，确保插入的是微控制器模块（ESP，如通常带有 Micro USB 的 Wemos D1 Mini），而不是充电模块（TP4056，通常带有 USB C）。
- 确保你的线缆是数据线。有些线缆仅用于充电，因此无法用于串行连接。
- 确保已安装相应的驱动程序。对于官方追踪器和大多数 DIY 追踪器，你需要 CH340/CH341 驱动程序。其他一些 DIY 追踪器需要 FT232 驱动程序。
  - CH340/CH341 驱动程序在安装 SlimeVR 时已安装，但也可在 <https://www.wch-ic.com/downloads/CH341SER_EXE.html> 找到。
    - 注意：某些 ESP 分线板（DIY）带有假冒的 CH340 芯片，无法与最新驱动程序配合使用。要解决此问题，你可以使用 <https://github.com/SHWotever/FakeCH340DriverFixer#how-to-use>（非 SlimeVR 提供，请小心使用）来自动检测这些假冒芯片并更正驱动程序版本。你也可以在同一页面上找到如何识别假冒芯片的信息。
  - FT232 驱动程序可在 <https://ftdichip.com/drivers/vcp-drivers/> 找到。
- 确保线缆已正确插入，通常会伴随咔嗒声表示已就位。

你可以使用设备管理器轻松确定芯片类型。打开设备管理器，在其中一个类别（通常为"端口 (COM 和 LPT)"或"其他设备"）下，你会看到以下之一：
- CH340："USB-SERIAL CH340"
- FT232："USB Serial Converter"

## 更新固件 / 尝试上传固件时提示"Please specify upload_port"

此错误表示计算机与追踪器之间存在干扰。请检查以下内容：

1. 确保追踪器的 USB 线缆已牢固插入 PC。
1. 确保你的 USB 线缆是数据和充电线（建议尝试其他线缆或使用该线缆连接其他设备进行测试）。
1. 确保驱动程序是最新的。
1. 你的 DIY 追踪器上可能有假冒的 CH340 模块。尝试运行 [FakeCH340DriverFixer](https://github.com/SHWotever/FakeCH340DriverFixer) 获取兼容的驱动程序。

此外，这可能是由软件占用 COM 端口引起的（**VSCode 和 Cura 可能是原因**）。

## Quest Pro 控制器导致高延迟 / 卡顿

Quest Pro 控制器可以使用 2.4 GHz Wi-Fi 连接到头显，这可能会与同样使用 2.4 GHz Wi-Fi 的 SlimeVR 追踪器产生干扰。目前最简单的解决方案是通过路由器更改 2.4GHz Wi-Fi 信道，但这可能并不总是有效。如果你想查找 Quest Pro 控制器的 Wi-Fi，它应该类似于"DIRECT-Meta-XXXX"。你可以阅读 [Meta 关于 Quest Pro 控制器 Wi-Fi 故障排除的支持文章](https://www.meta.com/help/quest/articles/getting-started/getting-started-with-quest-pro/wi-fi-troubleshooting-touch-pro-controllers/)了解更多信息。

## SlimeVR 服务端上磁力计值为 `0.0/0.0/0.0`

这是预期行为，由于 ESP8266 的硬件限制。
没有足够的时间来获取原始数据并发送到服务端，因为 ESP8266 使用位拆裂技术并且 I2C 事务的时间有限。
这并不意味着你的传感器已损坏或 SlimeVR 未使用磁力计传感器。

有关更多信息，请查看这个 [GitHub issue](https://github.com/SlimeVR/SlimeVR-Tracker-ESP/issues/510#issuecomment-3704191542)。

## 参考资料

* [BNO08X 校准文档](https://xdevs.com/doc/CEVA/BNO080-BNO085-Sesnor-Calibration-Procedure.pdf)
* [MPU-9250 产品规格](https://invensense.tdk.com/wp-content/uploads/2015/02/PS-MPU-9250A-01-v1.1.pdf)

*由 [calliepepper](https://github.com/calliepepper) 创建和更新，由 [emojikage](https://github.com/deiteris)、[spazzwan](https://github.com/Spazznyan)、[butterscotch.v](https://github.com/ButterscotchV)、[Smeltie](https://github.com/smeltie) 和 [Aed](https://github.com/Aed-1) 编辑。由 Amebun 大规模重新格式化和更新。*
