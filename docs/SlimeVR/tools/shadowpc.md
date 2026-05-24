# ShadowPC 与 SlimeVR

ShadowPC 是一种云计算机解决方案，通过使用您的 USB 外围设备提供无缝体验。
通过将所有内容卸载到云端，您不需要强大的游戏主机即可获得可玩的体验——只需一个良好的、低延迟的互联网连接。

------

## 如何将 SlimeVR 与 Shadow PC 一起使用

所需组件和软件：
- 支持虚拟桌面的 HMD，如 Quest 2 或 Quest 3。
- 有效的 Shadow PC 订阅。
- 一台 PC 或笔记本电脑（强烈建议使用以太网以获得更低延迟）。虽然也可以使用支持 Windows 10/11 热点功能的 USB Wi-Fi 适配器，但连接到与您的 slime 设备相同网络的以太网通常更可靠且延迟更低。
- 一份虚拟桌面许可证。
- 一个快速的双频 Wi-Fi 路由器。应配置一个 5GHz 频段给您的头显，以及 2.4GHz 频段给您的 slime 设备。
- 一个有效的 Tailscale 帐户。

设置步骤：
1. 在您的本地 PC 和 Shadow PC 上下载并安装 [TailScale](https://tailscale.com/download)。
2. 在两台设备上打开 Tailscale 并登录您的帐户。
3. 在您的 Shadow PC（而不是本地 PC）上下载、安装并打开 [SlimeVR](https://slimevr.dev/#download) 和 Virtual Desktop。
4. 确保您的追踪器已打开并连接到您的 Wi-Fi。您可以暂时在本地 PC 上安装 SlimeVR 以验证它们是否激活，但在继续之前请确保完全关闭。
5. 在您的本地 PC 上下载并打开 [SlimeFWD](https://github.com/ButterscotchV/SlimeFwd/releases/tag/v1.0.2)。
6. 从 Tailscale 复制 Shadow PC 的 IP 并粘贴到本地 PC 上的 SlimeFWD 中。
7. 在您的 Shadow PC 上打开 SlimeVR 并确认追踪器可见且正在更新。
8. 启动您的 VR 游戏。
9. 成功！

!!! note
    如果您使用的是基于 Smol/Receiver 的 Slime：
    将步骤 4 替换为将您的适配器/接收器插入 PC。
    将步骤 5 和 6 替换为使用 [EsbImuReceiverToLAN](https://github.com/Sebane1/EsbImuReceiverToLAN/releases/tag/1.4.0.0)

在虚拟桌面中禁用视频缓冲可能会改善延迟。
拥有快速的连接将提升您的体验。
上传速度和延迟对于良好的体验也非常重要。

*本指南由多位社区成员编写，ShadowPC 与 SlimeVR 无关联。*

*原始撰稿：blaineam，为文档使用而编辑：smeltie，根据最新的 ShadowPC 客户端更改由 blaineam 更新。根据社区测试和反馈由 Amebun 再次更新。*
