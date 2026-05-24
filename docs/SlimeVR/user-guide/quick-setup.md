# 快速设置

本指南旨在帮助你尽可能快速地设置**预构建的 Slime 追踪器**。如果你使用手机、DIY 追踪器或用非预构建设备替代某些身体部位，则会增加额外的复杂性。

## 目录

- TOC
{:toc}

## 确保系统就绪
如果你打算将 SteamVR 与你的 Slime 追踪器一起使用，请确保已安装 SteamVR 并**至少运行过一次**后再继续。

## 安装最新的 SlimeVR 安装程序
最新的 [SlimeVR 安装程序可以在此处找到。](https://slimevr.dev/download) 下载并安装它，此安装程序将来可用于更新服务端软件。

如果你在 Windows 上遇到以下弹出窗口，请点击 _**更多信息**_ 文本以显示运行按钮。显示后，点击 **仍要运行** 以继续。

<img src="assets/img/quick_protected.png" alt="Windows Defender" style="max-width:45%;margin: 0 2%;display: inline-block;" /><img src="assets/img/quick_runAnyway.png" alt="Windows Defender" style="max-width:45%;margin: 0 2%;display: inline-block;" />

如果这不能解决问题，请尝试通过右键单击文件，选择属性，然后勾选 **解除锁定** 复选框来解除文件锁定。

![Properties unblock](assets/img/quick_windowsProperties.png)

启动安装程序后，点击 **下一步 >** 以完成流程。确保不要更改预选中的安装包，以便与 SteamVR 配合使用。

![The Installer wizard](assets/img/quick_installer.png)

请注意，如果你计划仅通过 [OSC](../server/osc-information.md) 独立使用服务端，而不通过 SteamVR 在 PC 上使用 VR，则可以取消选择 **SteamVR 驱动程序**、**SlimeVR Feeder 应用** 和 **USB 驱动程序**。如果你尚未安装并启动过 SteamVR，可能会遇到错误。

## 连接和准备追踪器

### 视频指南
<div class="video-container">
<iframe width="100%" height="auto" src="https://www.youtube.com/embed/SkfdraicN5s" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay muted; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

### 文字指南

请注意，SlimeVR 追踪器只能连接到 2.4GHz 频段的 Wi-Fi 网络，你的主机（PC 或手机）需要连接到同一网络。
1. 打开 SlimeVR 服务端。在初始页面上，你可以通过右下角的按钮更改应用程序语言。准备就绪后，点击 **开始设置！**

   ![The first page of the SlimeVR Wizard](assets/img/quick_intro.png)

1. 输入你的 2.4GHz Wi-Fi 凭据，以便你的追踪器可以连接到 Wi-Fi，然后点击 **提交**。

   ![Inputting WiFi credentials](assets/img/quick_wifi.png)

1. 一次插入一个追踪器并打开电源，你应该看到左侧的进度条更新以显示 Wi-Fi 详细信息正在发送。确保使用追踪器附带的线缆，因为其他线缆可能不适合传输数据。

	![Animation of the connection process](assets/img/quick_connectTracker.gif)

1. 连接完所有追踪器后，你应该会在右侧看到它们以编号列表形式显示。如果你忘记了哪些追踪器尚未插入，摇晃已连接的追踪器会将其在列表中高亮显示。完成后点击 **我已连接所有追踪器**。

   ![Connect trackers page](assets/img/quick_trackerConnected.png)

1. 按照页面上显示的指示，将追踪器在通电状态下放置在平坦表面上，然后点击 **我已将追踪器放在桌子上**，等待过程完成。

	![Calibration page](assets/img/quick_calibrate.png)

	请注意：每次打开追踪器电源时，它们都需要执行此校准。每次使用追踪器时，打开电源后请务必将它们放在平坦表面上！

1. 校准完成后，点击 **继续** 以继续。

	![Calibration complete](assets/img/quick_calibrateComplete.png)

1. 按照页面上显示的指示，通过系上绑带和贴纸来装饰你的追踪器，以帮助你记住每个追踪器是为哪个身体部位设置的。所有追踪器准备就绪后，点击 **我已粘贴贴纸和绑带！** 以继续。

    ![Straps and Stickers page](assets/img/quick_prepare.png)

## 选择和分配身体部位

1. 确定你需要分配哪些身体部位。根据你拥有的追踪器数量，以下是建议的位置：

	* 下半身套装（5 个追踪器）- 胸部、双腿、双脚踝。
	* 核心套装（5 个追踪器带一个扩展）- 胸部和臀部/腰部（通过带有扩展的追踪器）、双腿、双脚踝。
	* 增强核心套装（5 个追踪器带三个扩展）- 胸部和臀部/腰部（通过带有扩展的追踪器）、双腿、双脚踝和脚部（通过带有扩展的追踪器）。
	* 全身套装（7 个追踪器带三个扩展）- 双上臂、胸部和臀部/腰部（通过带有扩展的追踪器）、双腿、双脚踝和脚部（通过带有扩展的追踪器）。

1. 使用此列表，在 SlimeVR 的吉祥物 Nighty 上选择与你想要选择追踪器的位置相对应的区域。

	![Tracker location page](assets/img/quick_assign.png)

1. 弹出窗口打开时，你可以双击要用于该位置的追踪器以自动分配。如果你觉得更方便，也可以在列表中选择要分配的特定追踪器。

	![Tracker list pop up for choosing the right tracker](assets/img/quick_assignPopup.png)

1. 分配完所有追踪器后，点击 **我已准备好** 以继续。

1. 花点时间戴上所有追踪器。你可以将其佩戴在标记位置的前面、后面或身体两侧，并注意以下建议：
	* 肌肉发达的区域容易变形并可能干扰追踪，请尽量找到能最小化此问题的位置。
	* Nighty 的图示应为你提供佩戴的大致区域，但你可以将位置绕身体旋转。例如，胸部追踪器根据衣物和体型，佩戴在正面或背面可能更舒适。
	* 确保你的追踪器与你的身体保持基本方向，它们必须面向**前**、**后**、**左**或**右**。
	* 确保追踪器方向正确，Slime 的脸应朝上，追踪器的平坦部分应朝向地面。
	* 戴上追踪器后，试着四处移动，看看它们是否在运动期间保持静止。某些区域（如脚踝）在脚踝侧面比正面效果好得多。
	* 每个人的身体都不一样！适合他人的安装方向可能不适合你，你可能需要尝试才能找到最适合你的位置。

	戴好追踪器后，点击 *我已准备好* 进入下一步。

1. SlimeVR 提供自动和手动两种方式来确定安装方向。自动校准可以带来更好的追踪质量，但不正确的校准可能使效果更差。这需要一些时间来确认它是否适合你和你的佩戴方式。我们正在努力改进它，但建议**新用户使用手动流程**。

	![Manual or Automatic mounting page](assets/img/quick_mountingChoice.png)

1. 点击其中一个追踪器以显示安装方向列表。

	![Manual mounting page](assets/img/quick_mountingManual.png)

1. 选择最能代表该追踪器安装方向的方向。

	![Manual mounting popup](assets/img/quick_mountingPopup.png)

1. 对每个追踪器重复此操作，完成后点击 **下一步**。

### 自动设置安装方向

SlimeVR 提供自动化流程来记录你设置的追踪器安装方向，这对新用户可能带来问题，但对有经验的用户可以带来更好的结果。从此时起，请确保启动 SteamVR 并戴上头显。如果你仅将追踪器用于 VMC 或 OSC，请使用之前的手动设置安装方向步骤。

在自动流程中，按照指示操作，SlimeVR 将推断你的追踪器在身体上的位置。

> **注意：** 如果你未佩戴头显且未运行 SteamVR，自动安装可能无法正常工作。自动安装可以带来更好的追踪质量，但不正确的校准可能使效果更差。仅当你对 SlimeVR 有经验时才选择此选项。

![The automatic process for determining facing location](assets/img/quick_mountingAuto.png)

## 重置教程

1. 按照流程了解追踪器内置的三种不同类型的重置：

	![Reset Tutorials](assets/img/quick_reset.png)

	* **轻拍胸部** - 偏航重置，重置追踪器使其假定朝向已定义的安装方向。
	* **轻拍左大腿** - 完全重置，重置追踪器以假定你处于 I 型站姿。
	* **轻拍右大腿** - 安装重置，将追踪器重置为估算的安装方向。此操作需要你处于安装校准向导中图示的滑雪姿势。

1. 要完成此流程，请按照所示步骤操作并轻拍指示的追踪器。

## 配置身体比例

1. 最后一个配置是让 SlimeVR 确定你的身体比例！这是复现你在虚拟空间中运动的关键步骤。

	![Manual or Automatic Proportions page](assets/img/quick_proportionsChoice.png)

	如果你将 SlimeVR 与 SteamVR 配合使用，可以自动化此过程。确保你佩戴了追踪器和头显，并且 SteamVR 正在运行。在此之前，确保头显的地面设置正确也非常重要。

	如果你未将 SlimeVR 与 SteamVR 配合使用，则需要[手动设置比例](#手动设置比例)。

1. 按照提示依次操作，让 SlimeVR 自动测量你的身体比例。

	> **注意：** 如果你未佩戴头显且未运行 SteamVR，自动比例测量将无法工作。在此过程中不要抬起或移动双脚。

   ![Automatic proportions wizard](assets/img/quick_proportionsAuto.png)

### 手动设置比例

如果你未使用 SteamVR，则必须手动设置这些值，或使用 VRChat OSC Query 来启用自动比例测量。有关如何测量每个值的更多信息，请参阅[身体比例配置页面](../server/body-config.html#measurements)顶部的信息。

![Manual proportions](assets/img/quick_proportionsManual.png)

有关如何设置 VRChat OSC Query 的更多信息，请参阅[移动端安装](../tools/mobile-installation.md)。

## 最终设置

最后一步是进入设置页面，配置具体的使用方式。

### 生成追踪器

SlimeVR 服务端现在具有 SteamVR 追踪器的自动分配功能，以下显示了开启此功能后每个套装将激活的内容：

* 下半身套装（5 个追踪器）- 胸部、腰部、膝盖和脚部。
* 核心套装（5 个追踪器带一个扩展）- 胸部、腰部、膝盖和脚部。
* 增强核心套装（5 个追踪器带三个扩展）- 胸部、腰部、膝盖和脚部。
* 全身套装（7 个追踪器带三个扩展）- 胸部、腰部、膝盖、脚部和肘部。

![SteamVR Settings](assets/img/quick_settingsPage.png)

## 在 SteamVR 上启用追踪器

1. 确保你已通过安装程序安装 SlimeVR，以获得正确的 SteamVR 驱动程序。
1. 确保在 SteamVR 设置 > 启动/关闭 > 管理附加组件中启用了 SlimeVR 插件。
1. 确保在 SlimeVR 设置中启用了 SteamVR 追踪器。

### OSC

如果你决定在 Steam 版 VRChat 中使用 OSC 追踪器，请确保在进入 OSC 设置之前禁用所有 SteamVR 追踪器。

![OSC Settings](assets/img/quick_oscSettings.png)

在这里，你需要确保网络地址设置正确。

#### 软件直接在 Quest 上运行
如果服务端[在 Quest 上运行](../tools/mobile-installation.md)，将地址保留为 127.0.0.1。

#### 软件在其他设备上运行（手机、笔记本电脑、旧 PC 等）
如果服务端不在 Quest 上，请输入你的 Quest 的 IP。你可以通过打开 Quest 上的快速设置菜单，选择 Wi-Fi，你当前连接的网络，向下滚动并点击箭头来获取。IP 地址列在那里。[关于如何查找 Quest IP 的视频教程](https://www.youtube.com/watch?v=gL1vgWubcJw)。

然后，你可以根据以下建议切换所需的位置：

* 下半身套装（5 个追踪器）- 腰部、膝盖和脚部。
* 核心套装（5 个追踪器带 1 个扩展）- 胸部、腰部、膝盖和脚部。
* 增强核心套装（5 个追踪器带 3 个扩展）- 胸部、腰部、膝盖和脚部。
* 全身套装（7 个追踪器带 3 个扩展）- 胸部、腰部、膝盖、脚部和肘部。

如果你想切换回 SteamVR 追踪器，必须先禁用 OSC 并重新开启 SteamVR 追踪器。

有关 OSC 的更多信息，请访问 [OSC 页面](../server/osc-information.md)。

## 恭喜，你的 Slime 追踪器现在已经设置好了！

![Setup complete page](assets/img/quick_allDone.png)

### 本次设置后再次佩戴

下次你想使用追踪器时，只需戴上它们并快速通过安装校准向导即可。所有其他设置应从初始设置中保存！在完成此过程之前，请确保你佩戴了头显并且 SteamVR 正在运行。

### 遇到问题？

**我的 SteamVR 中的追踪器设置不正确**

如果在启动任何游戏之前在 SteamVR 中出现此问题，请前往设置 > 控制器 > 管理 Vive 追踪器，并手动将追踪器的位置设置为与虚拟追踪器名称匹配。如果是在游戏中，则可能是校准问题！

**我的追踪器无法连接到 Wi-Fi**

如果你遇到 Wi-Fi 问题，可以尝试使用其他 Wi-Fi 网络或[使用 PC 托管热点](../server/alternate-wifi.md)。

对于所有其他问题，请查看[常见问题页面](common-issues.md)。
