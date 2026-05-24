# owoTrack 应用

owoTrack 是一款移动应用程序，可用于使用手机进行 VR 追踪。
该应用程序使用 SlimeVR Server 进行追踪。要设置 SlimeVR Server，请参阅 [SlimeVR 设置指南](../server/index.md)。

如果您使用追踪器/手机配合 owoTrack 应用进行追踪，全身追踪至少需要 5 个追踪器/手机。如果您只需要腰部追踪，可以使用一部手机。腰部追踪也可以配合 [owoTrack SteamVR 驱动](https://github.com/abb128/owo-track-driver) 使用，无需 SlimeVR。

您的 PC 和追踪器/手机应连接到同一个本地网络。

## 目录

* TOC
{:toc}

## 下载链接

Android 版本可在 Google Play 上获取：[https://play.google.com/store/apps/details?id=org.ovrgyrotrackersync](https://play.google.com/store/apps/details?id=org.ovrgyrotrackersync)

IOS 版本可在 App Store 上获取：[https://apps.apple.com/au/app/owotrack/id1563711037](https://apps.apple.com/au/app/owotrack/id1563711037)

由 ferdimarti#2111 创建

## 常见问题

### 进行腿部追踪需要多少个追踪器或手机？

使用 SlimeVR 进行 FBT 至少需要 5 个追踪器或手机。

### 我听说可以使用 3 部手机进行腿部追踪

不行。您将获得糟糕的体验，这不是我们的错。您的膝盖无法弯曲，整体体验会很差。最低要求是 5 个。

### 我只有一部/两部手机

您可以使用官方的 owoTrack 驱动进行腰部追踪，或使用 SlimeVR Server 进行腰部追踪（如果有两部手机，还可追踪胸部）。这不会追踪您的腿部。

### 我尝试运行 SlimeVR 但没有反应。为什么？

请参阅 [SlimeVR 设置指南](../server/index.md) 了解如何设置 SlimeVR。

### 我的追踪器已连接到 SlimeVR Server，但在 SteamVR 中没有动作

请确保您在 SlimeVR Server 中为追踪器/手机选择了正确的角色。它们应为腰部、左大腿、右大腿、左小腿和右小腿。

要了解如何设置追踪器角色，请参阅 [SlimeVR 设置指南](../server/index.md)。

### 我的控制器被识别为追踪器。如何解决？

您需要在 SteamVR 中为追踪器分配角色：

1. 在 SteamVR 中，进入**设置** > **设备** > **管理追踪器**。
2. 在追踪器列表中，找到名为 `/devices/SlimeVR/SlimeVRTracker#` 的追踪器，并从上到下依次分配 WAIST、LEFT_FOOT、RIGHT_FOOT 角色。
3. 重新启动 SteamVR。

要了解如何设置追踪器角色，请参阅 [SlimeVR 设置指南](../server/index.md)。

### 我应该以什么顺序启动 SteamVR 和 SlimeVR Server？

顺序无关紧要。

### 我的手机无法连接到服务器

请检查 IP 地址是否正确。

**您可以在 owoTrack Android 应用中将 IP 设置为 255.255.255.255**

要检查您的 IP 地址，您可以打开 PowerShell 窗口或命令提示符窗口（cmd.exe）并执行 `ipconfig` 命令，获取您的 PC IPv4 地址字段——例如 192.168.1.2，然后将其输入到 owoTrack 应用中。

如果您使用的是 iPhone，请检查 **OwOTrack** 是否可以与您本地网络上的设备通信。
您可以在**设置** > **隐私** > **本地网络**中找到此设置，确保 **OwOTrack** 旁边的开关已打开。

### 我有一台 iPhone，它会在 10 分钟后断开连接

Apple 对应用在后台的网络访问有限制。此问题的解决方案正在调查中。

临时解决方法：

1. 启用**引导访问**。您可以在**设置** > **辅助功能** > **引导访问**中找到此设置。
2. 禁用屏幕自动锁定。为此，请前往**设置** > **显示与亮度**，点击**自动锁定**并将其设置为**永不**。
3. 启动 owoTrack 应用。
4. 将屏幕亮度调至最低以节省电量。

### SteamVR 中的虚拟追踪器显示为灰色

这是正常行为，请检查追踪器是否在 VR 中存在。

### 其他问题

您可能还需要设置正确的防火墙规则，以使 owoTrack 正常工作。下载 [firewall.bat](../files/firewall.bat)，将其移动到一个名称中没有空格或符号的目录，然后以管理员身份运行该 bat 文件。

*由 adigyran 在 mightygood 的帮助下创建，由 calliepepper 和 emojikage 编辑和设计样式。*
