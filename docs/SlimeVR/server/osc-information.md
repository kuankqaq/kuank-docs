# OSC（独立追踪）

OSC 代表 Open Sound Control（开放式声音控制）。它最初是为了以一种简单、开放和标准的方式连接和控制音乐设备而开发的。VRChat 开发了一个系统，用于控制人物模型和虚拟追踪器，从而在任何支持[独立 VRChat](https://wiki.vrchat.com/wiki/Getting_Started#Standalone_devices) 的头显上实现全身追踪。您可以在此处阅读 VRChat 的相关文档：[https://docs.vrchat.com/docs/osc-overview](https://docs.vrchat.com/docs/osc-overview)。

# 兼容的头显

以下是截至撰写本文时官方支持独立 VRChat 的头显列表。
要获取最新的完整列表，您可以查看 VRChat 的官方 wiki：[https://wiki.vrchat.com/wiki/Getting_Started#Standalone_devices](https://wiki.vrchat.com/wiki/Getting_Started#Standalone_devices)

- Meta Quest 2
- Meta Quest 3
- Meta Quest 3S
- Meta Quest Pro
- Vive Focus Vision
- Vive XR Elite
- Pico 4
- Pico 4 Pro
- Pico 4 Ultra

# OSC 设置

设置好追踪器并正确安装后，您可以设置 OSC。在 SlimeVR Server 中，导航至设置 > OSC > VRChat OSC Trackers，然后启用 OSC。

### 在 Quest 上直接运行软件
如果服务器[在 Quest 上运行](../tools/mobile-installation.md)，将地址保留为 127.0.0.1。

### 在其他设备上运行软件（手机、笔记本电脑、旧 PC 等）
如果服务器不在 Quest 上，请输入您 Quest 的 IP。您可以通过打开 Quest 上的快速设置菜单，选择 Wi-Fi，您当前连接的网络，向下滚动并点击箭头来获取此 IP。IP 地址列在那里（[如何找到 Quest IP 的视频教程](https://www.youtube.com/watch?v=gL1vgWubcJw)）。

![image](https://github.com/user-attachments/assets/c6f43e36-882d-4146-ad1e-eaf441ec9437)

现在 SlimeVR 端已设置完成，您可以将 VRChat 连接到 SlimeVR。

**如果应用程序直接在您的 Quest 上运行，请立即执行完整重置**

在您的 Quest 上打开 VRChat。

使用径向菜单，选择顶部的选项，然后选择 OSC，然后启用它。
您可以通过选择"OSC Debug"来验证 VRChat 是否能看到追踪器。

![img](https://user-images.githubusercontent.com/737888/154179201-ec413948-7013-494a-81fb-4b5e1129cf5f.jpg)

走到镜子前，打开快速菜单，然后按"Calibrate FBT"。做一个 T-Pose，与镜子中的 T-Pose 对齐。在服务器上按重置（除非您在 Quest 上运行它）。扣动两个扳机，大功告成！

注意：如果 SlimeVR 在您的 Quest 上运行且追踪器初始位置不对齐，您可以导航到 VRChat 快速菜单中的 IK 设置，并按一次或两次"Auto-Center OSC Trackers"。

*由 lordbagel42、Smeltie 创建。SlimeVR OSC 实现由 erimel 完成。*
