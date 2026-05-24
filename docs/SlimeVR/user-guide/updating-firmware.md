# 更新追踪器固件

在本页面中，你将找到几种刷写 SlimeVR 追踪器的方法，以及如何手动恢复官方 SlimeVR 追踪器。

## 索引
- [更新你的 SlimeVR 追踪器](#更新你的-slimevr-追踪器) - 如何更新官方 SlimeVR 追踪器。
- [USB 恢复](#usb-恢复) - 在更新失败后恢复追踪器。
- [手动无线更新](#手动无线更新) - 回滚固件。

# 更新你的 SlimeVR 追踪器

在正常情况下，应使用主菜单中追踪器上出现的图标来更新官方 SlimeVR 追踪器。

![update](assets/img/Official_Tracker_Update.png)

!!! warning
    请注意，此过程需要将追踪器充电至至少 50%。

![updatelowbattery](assets/img/Official_Tracker_Update_Low_Battery.png)

点击更新图标后，你应该会看到以下画面，请选择要更新的追踪器并点击"更新所选追踪器"。

![update1](assets/img/Official_Tracker_Update_1.png)

现在，关闭再重新打开要更新的追踪器！

!!! warning
    除非被告知，否则请勿在上传过程中拔掉或关闭追踪器，否则可能导致追踪器无法使用。

![update2](assets/img/Official_Tracker_Update_2.png)

现在，软件将固件上传到所选的追踪器。

![update3](assets/img/Official_Tracker_Update_3.png)

接下来，软件将对所选追踪器应用更新后的固件。

![update4](assets/img/Official_Tracker_Update_4.png)

就是这样！你的追踪器现在应该已更新到最新版本！

![update5](assets/img/Official_Tracker_Update_5.png)

现在，关闭再重新打开要更新的追踪器！

!!! warning
    如果追踪器在更新后停止工作，请勿刷写其他追踪器，并参考下面的 USB 恢复部分来恢复追踪器固件。

## 免责声明

!!! danger
    以下链接的步骤是针对官方 SlimeVR 追踪器定制的，所显示的设置不适用于大多数 DIY 追踪器！
    此方法有可能损坏你的追踪器，请仔细阅读以下警告：
    
    1. 在刷写或应用更新过程中，请勿关闭追踪器。
    
    2. 刷写后，在关闭追踪器之前确保其功能正常。
    
    3. 如果追踪器在无线刷写后停止工作，请先尝试通过 USB 恢复进行修复，然后再继续处理其他追踪器。
    
    4. 上传非官方/不支持的固件可能会影响追踪器的功能，并可能使保修失效。

# USB 恢复

此方法仅在无线 (OTA) 更新不可用时使用。
在此过程中你需要拆解追踪器，**这不会使保修失效。**

!!! warning
    此方法需要以下物品：
     - 一根支持数据传输的 USB-C 线缆（附带的线缆应该足够）。
     - 一把全尺寸 PH1（十字）螺丝刀（精密套装可能会损坏螺丝）。
     - 导电工具，如镊子或回形针，用于桥接指定点（仅 R11 和 R12 需要，R14 有一个物理按钮）。

*如果螺丝滑丝，你可以使用橡皮筋，这是取出滑丝螺丝的常用方法*

## 拆解追踪器

首先关闭追踪器并取下绑带。使用**米字**螺丝刀（JIS 和十字头可能可用，但可能损坏螺丝）拧下追踪器背面的螺丝。

![Tracker Screw Disassembly](assets/img/Tracker_Unscrew.png)

取下后盖后，可以小心地取出电池并放在一边。然后，通过抬起 PCB 的后侧（电源开关和 USB 端口的对面）来轻轻倾斜取出 PCB。

!!! warning
    确保不要触摸后侧左侧的黑色天线。因为它可能很脆弱！

![Tracker Disassembly](assets/img/Tracker_Disassemble.png)

检查 PCB 背面以确定你的版本。

![Tracker PCB Revision](assets/img/Board_Identification.png)

## 通过 USB（串行）刷写

你可以在 SlimeVR 软件的设置菜单中找到"DIY 固件工具"。

如果你使用的是官方 SlimeVR 追踪器，对于 v1.0 或 v1.1 基于 BNO 的追踪器，选择"SlimeVR"；对于 v1.2 基于 ICM 的追踪器，选择"SlimeVR v1.2"，然后选择固件源"SlimeVR-Tracker-ESP"。

![step1](assets/img/Tracker_Flashing_1.png)

通过选择列表中数字最高的版本并点击"下一步"来选择最新的可用固件。

![step2](assets/img/Tracker_Flashing_2.png)

在此步骤中，需要插入追踪器（但暂时不要打开电源）。
要通过 USB 刷写追踪器，请选择"serial"，输入你的 Wi-Fi 凭据，然后从下拉菜单中选择检测到的串行设备（应为"USB-SERIAL CH340"）。

!!! warning
    Wi-Fi 名称和密码均区分大小写！

![step3](assets/img/Tracker_Flashing_4_SRL.png)

现在，在下一步中，你需要通过以下方式将追踪器启动到引导加载程序模式。
如果你在通电时使用此方法使蓝色 LED 快速闪烁一次，则说明操作正确（在此阶段追踪器需要保持插入状态）。

!!! warning
    PCB 的版本，标注为 R1x，可在 PCB 背面找到，对下一步操作很重要！

| 版本 | 步骤 |
|-----------|------------------------------------------------------------------------------------|
|    R11    | 在打开追踪器电源的同时，将电路板顶部边缘的第二个矩形 FLASH 焊盘与微控制器的金属屏蔽层短接。 |
|    R12    | 在打开追踪器电源的同时，将电路板顶部的圆形 FLASH 焊盘与微控制器的金属屏蔽层短接。 |
|    R14    | 在打开追踪器电源的同时按住电路板顶部的 FLASH 按钮，打开电源后即可松开。 |

![Tracker R11](assets/img/R11_board_reset.png)
![Tracker R12](assets/img/R12_board_reset.png)
![Tracker R14](assets/img/R14_board_reset_sw.png)

现在点击"下一步"，它应进入以下屏幕，与 MCU 进行同步。
如果失败，你可能需要点击重试。如果仍无法解决，请重新执行上述步骤，确保它处于引导加载程序模式（在引导加载程序模式下通电时，蓝色 LED 应快速闪烁一次）。

![step8](assets/img/Tracker_Flashing_8.png)

更新现在应已应用到追踪器。

!!! danger
    在应用更新时请勿关闭追踪器！

![step9](assets/img/Tracker_Flashing_9.png)

更新现在应已完成！
如果出现错误，请尝试点击重试。如果仍无法解决问题，你可能需要重新开始。

![step10](assets/img/Tracker_Flashing_10.png)

最后，关闭再重新打开追踪器以重新连接到软件。你可以对任何其他需要恢复的追踪器重复此过程。

# 手动无线更新

此方法无需拆解追踪器或使用任何线缆，但要求你的追踪器已连接到 Wi-Fi 网络。
你可以在 SlimeVR 软件的设置菜单中找到"DIY 固件工具"。

如果你使用官方 SlimeVR 追踪器，请选择"SlimeVR"并点击"下一步"。

![step1](assets/img/Tracker_Flashing_1.png)

从列表中选择版本号，然后点击"下一步"，选择最新可用或所需的固件。

![step2](assets/img/Tracker_Flashing_2.png)

要通过无线方式刷写追踪器，请选择"OTA"，然后选择要刷写的所有追踪器。
在此步骤中，你的追踪器需要已开机并连接到 Wi-Fi。选择所有所需的追踪器后，点击"下一步"。

![step3](assets/img/Tracker_Flashing_3_OTA.png)

在此步骤中，你需要关闭再重新打开追踪器，这样我们就可以验证 OTA 已启用并开始刷写追踪器。

!!! warning
    如果工具显示"超时"，你需要点击"重试"并按照屏幕上的指示操作。

![step5](assets/img/Tracker_Flashing_5.png)

追踪器现在将开始更新。

!!! danger
    刷写时请勿关闭追踪器！

![step6](assets/img/Tracker_Flashing_6.png)

追踪器现已更新，可以使用了！

![step7](assets/img/Tracker_Flashing_7.png)

!!! danger
    如果追踪器在刷写后停止工作，请勿刷写其他追踪器，并参考上面的 USB 刷写部分进行恢复。

*由 [Smeltie](https://github.com/smeltie) 和 [Meia](https://github.com/Kounocom) 创建。*
