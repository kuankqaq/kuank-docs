<link rel="stylesheet" href="slimevr101.css">

# SlimeVR 101

## 什么是 SlimeVR？

SlimeVR 是一种经济实惠的虚拟现实全身追踪解决方案。它使用正向运动学[^note]根据每个追踪器的旋转来计算其位置，从而创建你的身体模型。
唯一的固定点是你的头显，它作为主要的参考位置。

由于头显是唯一固定的数据点，SlimeVR 不需要像 Lighthouse 那样的额外追踪设备。它依靠惯性测量单元 (IMU) 来追踪每个设备的旋转。使用的 IMU 越多，可用于追踪身体的数据点就越多。

[^note]: 正向运动学是根据骨骼角度计算身体部位（如脚或手臂）位置的过程。根据你的关节（如膝盖或肘部）的定位方式，正向运动学可以判断你的脚或手臂在空间中的位置。这就像弄清楚当你以某种方式弯曲腿时，你的脚会去哪里。

## SlimeVR 兼容性

我们经常遇到的一个问题是："SlimeVR 与我的硬件兼容吗？"简而言之，SlimeVR 与**任何**连接到 **SteamVR** 的头显兼容，以及任何可以运行 [VRChat 独立版](https://wiki.vrchat.com/wiki/Getting_Started#Standalone_devices)的头显。
SlimeVR 还支持通过其自身的传感器融合系统使用其他追踪器和估算软件。
你可以在[这里](../misc/compatibility.md)找到更详细和全面的兼容性列表。

## 你需要多少个追踪器？

每个追踪器测量一根骨骼的旋转，当所有骨骼的数据组合在一起时，就会创建出你实际姿态和动作的模拟。因此，你应该使用足够数量的追踪器来满足你的特定全身追踪需求。

<div class="embeddedVideo">
	<video name="Tracking Example" playsinline autoplay muted loop>
	  <source src="./assets/videos/ostriches.webm" type="video/webm">
	  <source src="./assets/videos/ostriches.mov" type="video/quicktime">
	</video><br>
	动图由 Butterscotch 提供。舞蹈由 ToriKari 提供。每条线代表一个被追踪的"骨骼"。
</div>

根据你计划在 VR 中使用 FBT 的方式，选择以下选项之一：

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>套装变体</th>
        <th>IMU 数量</th>
        <th>相比上一套增加的追踪器</th>
        <th>预期用户</th>
        <th>优势</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>下半身套装</td>
        <td data-label="IMU 数量：">5</td>
        <td data-label="追踪器位置：">脊椎、膝盖、脚踝</td>
        <td data-label="预期用户：">休闲 VR 用户</td>
        <td data-label="优势：">
          提供腿部和脊椎的位置追踪。对脚部方向和脊椎下弯的追踪有限。
        </td>
      </tr>
      <tr>
        <td>核心套装</td>
        <td data-label="IMU 数量：">6</td>
        <td data-label="追踪器位置：">+ 额外脊椎追踪器</td>
        <td data-label="预期用户：">
          希望获得臀部旋转并提高躯干运动准确度的用户
        </td>
        <td data-label="优势：">
          在臀部增加一个额外的脊椎追踪器以提高稳定性，尤其是在坐着、躺着或弯腰时。
        </td>
      </tr>
      <tr>
        <td>增强核心套装</td>
        <td data-label="IMU 数量：">8</td>
        <td data-label="追踪器位置：">
          + 脚部方向（额外脚部追踪器）
        </td>
        <td data-label="预期用户：">
          经常坐着或躺着的用户
        </td>
        <td data-label="优势：">
          增加脚部运动追踪，实现坐着或躺着时更具表现力和情感的姿态。
        </td>
      </tr>
      <tr>
        <td>全身套装</td>
        <td data-label="IMU 数量：">10</td>
        <td data-label="追踪器位置：">+ 肘部</td>
        <td data-label="预期用户：">
          舞者、角色扮演者、沉浸式用户
        </td>
        <td data-label="优势：">
          实现独立的肘部运动，提供更真实的上半身运动并增加 VR 沉浸感。
        </td>
      </tr>
      <tr>
        <td>豪华追踪器套装</td>
        <td data-label="IMU 数量：">16</td>
        <td data-label="追踪器位置：">完全可定制</td>
        <td data-label="预期用户：">
          动作捕捉专业人士、动画师
        </td>
        <td data-label="优势：">
          可无需 VR 设备用于动作捕捉，拆分为两套增强核心套装，或根据需要进行定制，以实现灵活性和精度。
        </td>
      </tr>
    </tbody>
  </table>
</div>

如需更多关于这些追踪选项样式的视觉效果，请观看此视频：

<div class="video-container">
  <iframe
    width="100%"
    height="auto"
    src="https://www.youtube.com/embed/KN3dxGNAq34"
    title="YouTube video player"
    frameborder="0"
    allow="
      accelerometer;
      autoplay muted;
      clipboard-write;
      encrypted-media;
      gyroscope;
      picture-in-picture;
    "
    allowfullscreen
  ></iframe>
</div>

## 什么是扩展？

扩展是连接到主追踪器并放置在另一个位置的单个辅助 IMU。这让你无需额外的电池、充电板和微控制器即可构建次级追踪器。有时被称为 AUX 追踪器（辅助追踪器）。

扩展使得追踪具有两个紧密弯曲点的区域（如下腿和脚）成为可能，而无需另一个需要单独充电和通信的追踪器。

![Extension Image](assets/img/extension.jpg)<br>
*由 erimel 提供的开发套件图片*

扩展的长度取决于用于连接它们的线缆（短于 80cm 是安全范围）。更多信息请[查看追踪器原理图页面](../diy/tracker-schematics.md)。

建议的扩展位置如下：

1. 连接胸部追踪器的臀部扩展。
1. 连接左脚踝追踪器的左脚扩展。
1. 连接右脚踝追踪器的右脚扩展。

在 Crowd Supply 商店页面和我们的 Discord 服务器上，你可能会看到使用加号表示主 IMU 和辅助 IMU 数量的标记。例如，上面提到的增强核心套装被称为 6+2 配置，即 6 个微控制器和 8 个 IMU。要更直观地了解其佩戴效果，请查看[服务端设置中的推荐安装点部分](../server/putting-on-trackers.md#recommended-mounting-points)。

请注意：构建扩展并非必要，如果你愿意，脚和臀部位置可以由独立追踪器提供。但是，本文档假设你将其构建为扩展。

*由 calliepepper 创建。由 Amebun、spazzwan 和 [Depact](https://github.com/Depact) 编辑。视频由 zrock35 制作。*
