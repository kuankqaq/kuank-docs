# DIY 追踪器指南
本指南将帮助你从头开始构建 SlimeVR 追踪器。

如果你购买了 SlimeVR DIY 套件，请参阅 [DIY 套件页面](diy_kit_guide.md)。

如果你是第一次制作 DIY SlimeVR 追踪器，DIY 社区建议构建：
- [meowCarrier 追踪器](https://github.com/Shine-Bright-Meow/meowCarrier)（基于 Wi-Fi）
- [smol 追踪器](../smol-slimes/index.md)（基于 nRF）

!!! warning
    强烈建议使用基于 PCB 的构建方案，而非有线构建。有线构建更容易出错，更容易短路，并且由于线缆疲劳或断开，机械可靠性通常较低。

## 流程

开始之前，先决定[你可能需要多少追踪器](../user-guide/slimevr101.md#how-many-trackers-do-you-need)。

接下来，你需要决定是否使用[扩展模块](../user-guide/slimevr101.md#what-is-an-extension)。

!!! warning
    DIY 社区不鼓励使用扩展模块：
    - 扩展线缆即使在正常游戏过程中也容易断裂。
    - 一些微控制器（例如 Wemos D1 Mini 等 ESP8266）处理两个现代 IMU（如 ICM-45686）的数据时速度不够快，导致追踪器漂移严重。

确定所需追踪器和扩展模块数量后，可以开始以下步骤：

**1. 采购组件**

你需要购买项目所需的零件。相关指南请参阅我们的[组件指南页面](components-guide.md)。在此步骤中有多种选择，建议通读指南以了解每个组件的作用。请注意，本文档假设你使用的是该项目最常用的微控制器——Wemos D1 Mini。你也可以使用其他符合规格的微控制器，但相关文档没有这么全面。

> 请注意，如果你正在寻找 BNO085，SlimeVR 已不再销售。
> 如果你正在寻找 ICM-45686，可在 [SlimeVR 商店](https://shop.slimevr.dev/products/slimevr-mumo-breakout-module-v1-icm-45686-qmc6309)找到。

**2. 打印/购买外壳**

许多 DIY 爱好者使用特百惠、Tic Tac 或 jiffy 盒子，但社区也创建了一些[3D 打印文件](cases.md)。你也可以设计自己的 3D 打印外壳。

**3. 组装追踪器**

请参考我们的[追踪器原理图页面](tracker-schematics.md)。输入你采购的零件信息，根据生成的图片焊接追踪器。我们正在编写更详细的步骤说明。
快速焊接指南请参考以下视频：

<div class="video-container">
<iframe width="100%" height="auto" src="https://www.youtube.com/embed/P0YX_eKyfxA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay muted; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

**快速提示！**

大多数廉价烙铁会附带一卷焊锡，但通常质量较差，是有铅且不含松香芯的焊锡。

为获得最佳效果，建议购买无铅松香芯焊锡。

有铅焊锡虽可使用，但出于健康和安全考虑，不建议使用。

首次使用前（以及每次使用之间），请给烙铁头上锡。

- 只需加热烙铁，在烙铁头上充分添加焊锡。
- 然后用湿海绵或铜/钢丝球（或烙铁附带的清洁工具）擦拭烙铁头。
- 这将保护烙铁头，使其保持最佳工作状态。

**4. 上传固件**

从我们的 GitHub 下载固件，定义追踪器中使用的板和配置，然后刷写到新构建的追踪器中。完整步骤请参阅[上传固件指南](../firmware/index.md)。

**5. 安装和设置 SlimeVR 服务器**

最后一步需要安装和配置服务器，以便在电脑上使用追踪器。这些步骤可在我们的 [SlimeVR 服务器设置页面](../server/index.md)中找到。

*由 calliepepper 创建。由 Amebun 编辑。*
