# Smol 追踪器焊接

本页面提供两种学习焊接 Smol 追踪器的方法：视频教程和逐步文字指南。选择最适合您的方式！

## 目录

* TOC
{:toc}


## Lyall 的焊接视频教程

如果您更喜欢观看演示，可以跟随下面的视频学习。

<div class="video-container">
  <iframe
    width="100%"
    height="auto"
    src="https://www.youtube.com/embed/nlxK9ISl_DQ"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin"
    allowfullscreen
  ></iframe>
</div>

## Depact 的焊接文字教程

### 所需工具

#### 必备工具
- 斜口钳
- 镊子（用于固定按钮和排针）
- 烙铁
- 焊接海绵（用于清洁烙铁头）
- 松香芯焊锡丝（推荐使用，比单独使用焊锡和助焊剂更方便）
- 剪刀（用于切割金手指胶带）

#### 可选附加工具

- 焊接夹具（可选，但可使固定板卡更容易）
- 焊接垫（可选，保护您的工作台）

### PCB 焊接缺陷类型及解决方法

PCB 焊接及识别焊接缺陷和正确焊点的视觉指南。

<div class="embeddedVideo">
   <img src="..\assets\img\soldering\Rayming-SMT-Through-Hole-Soldering.jpg" loading="lazy" class="big-size-image"/>
   <br/>
   图片来源：[RayPCB](https://www.raypcb.com/pcb-soldering/)
</div>

### 焊接步骤

1. **焊接按钮**
   - 在按钮触点下方的通孔中预先填充焊锡。
   - 将按钮放在已填充焊锡的孔上。
   - 用烙铁加热该区域，直到焊锡牢固地连接按钮焊盘。
   <img src="..\assets\img\soldering\depact-soldering-guide\1.webp" loading="lazy" class="big-size-image"/>

2. **焊接可折断排针**
   - 从可折断排针条上折断一段 6 个引脚。
   - 将排针插入通孔，使其略微向板卡中心倾斜以固定。
   - 逐个焊接每个引脚，确保它们保持笔直且牢固连接。
   <img src="..\assets\img\soldering\depact-soldering-guide\2.webp" loading="lazy" class="big-size-image"/>

3. **绝缘 IMU**
   - 在 IMU 模块背面覆盖金手指胶带以防止短路。
   <img src="..\assets\img\soldering\depact-soldering-guide\3.webp" loading="lazy" class="big-size-image"/>

4. **将排针焊接到 IMU**

!!! warning
    本教程展示如何焊接 ICM-45686。对于其他 IMU，请参阅 [Smol 追踪器原理图](./smol-tracker.html#schematics)。

   - 将一排可折断排针焊接到 IMU 的一侧。
   <img src="..\assets\img\soldering\depact-soldering-guide\4.webp" loading="lazy" class="big-size-image"/>
   - 以略微倾斜的角度焊接另一侧的排针，使其与 IMU 焊盘良好接触。
   <img src="..\assets\img\soldering\depact-soldering-guide\5.webp" loading="lazy" class="big-size-image"/>

5. **修剪和检查排针**
   - 使用斜口钳修剪排针的多余长度。
   - 检查焊点，如有需要可添加更多焊锡，但避免过热，因为这可能使引脚松动。
   <img src="..\assets\img\soldering\depact-soldering-guide\6.webp" loading="lazy" class="big-size-image"/>

6. **焊接天线改装和电池**
   - 将天线 wire 和电池引线焊接到各自的焊盘上。
   - **为获得最佳性能，天线 wire 应剪至 31.2 mm。任何偏差都会降低性能。**
   <img src="..\assets\img\soldering\depact-soldering-guide\7.webp" loading="lazy" class="big-size-image"/>

在给板卡通电之前，仔细检查每个连接。

在串行终端中使用 `info` 命令检查 IMU 是否被检测到。如果未检测到，通常意味着存在焊接问题，或者较少见的情况是硬件故障。

<hr/>

## 附加材料

### Ibis 焊接夹具

<img src="..\assets\img\soldering/Ibis-IMU-Soldering-fixture.webp" loading="lazy" class="small-size-image"/>

您可以选择使用 Ibis 焊接夹具在焊接时固定 IMU 和排针。
注意：此夹具并非适用于所有 IMU，它专门设计用于 Deyta's Moffshop 的 LSM6DSR/LSM6DSV 和 SlimeVR Store 的 ICM-45686。

[下载 STL 文件](https://github.com/brisfknibis/ibis-trackers/blob/main/3D%20Print%20Models/Solder%20Cube.stl)

<hr/>

*由 Shine Bright ✨ 和 [Depact](https://github.com/Depact) 创建*
