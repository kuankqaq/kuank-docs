# 设置重置绑定

重置绑定是为增强体验而需设置的最重要功能之一。
它使您能够在几秒甚至更短的时间内完成重置。
在本指南中，我们将向您展示如何设置它们。

## 什么是重置？

重置是将 SlimeVR 骨架模型恢复为默认姿势的操作。
这是为了减轻您随时间可能遇到的任何漂移问题。
您可以选择完全重置或偏航重置，具体使用哪种取决于您的情况。
完全重置是完整的重置，您需要站直、向前看并执行重置（使用标准的 6 点追踪时无需 T-Pose）。
偏航重置用于清除漂移，仅重置发生漂移的轴。
现在您知道什么是重置了，让我们设置一个快速触发这些重置的方法吧！

## 使用哪种重置类型？

重置类型完全取决于您的位置或情况。

### 完全重置：

标准重置用于将您的骨架模型完全恢复到默认姿势。
执行方法是站直、向前看并执行重置。
这只有在站立时才能按预期工作。

### 偏航重置

偏航重置仅重置/修正一个轴上的任何潜在漂移。
虽然精度较低，但这允许您在坐着或躺着时进行重置。
建议在操作时伸直四肢并向前看，以获得最佳效果。
这种方法使您无需每次重置时都站起来。

## Feeder App

要设置 SlimeVR 的重置绑定，您可以使用 [Feeder App](https://github.com/SlimeVR/SlimeVR-Feeder-App)，它默认包含在 SlimeVR 安装程序中。
如果您运行的 SlimeVR 版本较旧且没有 Feeder App，您可以下载[最新版本](https://slimevr.dev/download)并安装。
这大大简化了重置绑定的设置。
您可以使用随附的视频作为视觉指南，了解如何设置重置绑定。

### 设置

要通过 Feeder App 设置重置绑定，请执行以下操作：

1. 打开 SteamVR 设置（确保已启用"高级设置"）。
2. 转到控制器 > "显示旧绑定 UI" > "显示更多应用程序"。
3. 向下滚动并选择 "SlimeVR-Feeder-App"。
4. 选择控制器上的一个按键用于重置绑定。
5. 现在您可以设置组合键或行为来执行："重置"或"偏航重置"。（请参考视频说明）

设置完成！
现在您已经设置好了，可以快速进行偏航重置了。
_西部的快速重置。_

您可以根据自己的喜好进行设置！
大多数人选择双击、长按或组合键/和弦。
这个选择完全取决于您。

<div class="video-container">
<iframe width="100%" height="auto" src="https://www.youtube.com/embed/iTOyCOT44d0" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay muted; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

## 键盘快捷键

SlimeVR Server 有以下默认按键绑定：

- `CTRL+ALT+SHIFT+U` 快速重置
- `CTRL+ALT+SHIFT+Y` 完全重置
- `CTRL+ALT+SHIFT+I` 安装重置
- `CTRL+ALT+SHIFT+O` 暂停追踪

这些按键绑定可以通过编辑 `vrconfig.yml` 文件中的以下行来配置：

```yaml
keybindings:
  fullResetBinding: "CTRL+ALT+SHIFT+Y"
  yawResetBinding: "CTRL+ALT+SHIFT+U"
  mountingResetBinding: "CTRL+ALT+SHIFT+I"
  pauseTrackingBinding: "CTRL+ALT+SHIFT+O"
```

如果您想将这些绑定到您的控制器，您需要一个额外的应用程序，例如：

- [OVR Advanced Settings](https://store.steampowered.com/app/1009850/OVR_Advanced_Settings/)（Steam 上 $7.99 USD 或 [GitHub](https://github.com/OpenVR-Advanced-Settings/OpenVR-AdvancedSettings) 上免费）
- [OVR Toolkit](https://store.steampowered.com/app/1068820/OVR_Toolkit/)（Steam 上 $12 USD）

### OVR Advanced Settings 绑定

请确保在按照以下步骤操作之前关闭 OVR Advanced Settings，否则您将遇到问题。

1. 在 Windows 资源管理器窗口中，在**地址栏**中输入 `%appdata%/AdvancedSettings-Team/OVR Advanced Settings.ini` 并按 Enter。应会打开包含 `OVR Advanced Settings.ini` 文件内容的记事本。
2. 找到 `keyboardOne`、`keyboardTwo` 和 `keyboardThree` 行，并将其替换为以下行：

   ```ini
   keyboardOne=^*>y ; CTRL+ALT+SHIFT+Y - 重置
   keyboardTwo=^*>u ; CTRL+ALT+SHIFT+U - 快速重置
   keyboardThree=^*>i ; CTRL+ALT+SHIFT+I - 安装重置
   ```

   > **注意：** 如果您更改了默认的 SlimeVR Server 按键绑定，请参考[键盘输入指南](https://github.com/OpenVR-Advanced-Settings/OpenVR-AdvancedSettings/blob/master/docs/keyboard_input_guide.md)。

3. 在 SteamVR 仪表板中，打开 OVR Advanced Settings 并选择 **绑定**。如果您在仪表板上看不到 OVR Advanced Settings 的图标，请尝试从 Steam 库中运行 OVR Advanced Settings，然后检查图标是否出现在仪表板上。
4. 在打开的窗口中，选择 **杂项** 选项卡。
5. 双击所需按键名称旁边的加号以添加绑定。
6. 在打开的对话框中，选择 **按钮**。
7. 点击所需按键操作旁边的 **无**。要查看更多按键操作，请单击 **显示更多**。
8. 在打开的 **布尔操作** 窗口中，选择 **键盘快捷键一**。
9. 对 **键盘快捷键二** 和 **键盘快捷键三** 重复前两个步骤。

<div class="video-container">
<iframe width="100%" height="auto" src="https://www.youtube.com/embed/KuCjmHBpH7E" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay muted; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

### OVR Toolkit

如果您不想将键盘快捷键直接绑定到控制器按钮上，OVR Toolkit 的"腕表"具有宏功能，可用于触发重置和快速重置。

演示 GIF：

<div class="embeddedVideo">
   <video name="重置绑定演示视频" autoplay muted loop playsinline>
      <source src="../assets/videos/ovrtDemo.webm" type="video/webm">
      <source src="../assets/videos/ovrtDemo.mov" type="video/quicktime">
   </video><br>
</div>

1. 打开 OVR Toolkit 设置，它可能在系统托盘中。<br>
   <img src="../assets/img/ovrSys.png" alt="系统托盘位置" class="small-size-image" />
2. 点击顶部的"设置"，然后点击右侧的"设置腕部宏"。
3. 点击底部的"宏图标"，这将打开一个文件夹，您可以将自定义宏图标的 PNG 文件放入其中。下载并复制这两个重置图标文件到该文件夹。<a href="../assets/img/resetBold.png" download>重置图标</a>。<a href="../assets/img/quickresetBold.png" download>快速重置图标</a>。
4. 点击"添加宏"，然后点击"添加按键"直到您为绑定的每个键都有了足够的按键位。（默认需要 4 个）。
5. 对于序列中的每个键，点击"重新绑定"，然后按一次绑定的其中一个按钮。确保字母在最下面的键位置很重要，因为这是按键按下的顺序。输入 `Y+CTRL+ALT+SHIFT` 是无效的，但 `CTRL+ALT+SHIFT+Y` 是有效的。
6. 点击条目左侧的空白图标方块，然后选择相应的图标。（区分：重置是基本重置符号。快速重置中间有火焰标记。）
7. 对另一个绑定重复步骤 5-7。
8. 点击"保存更改"，然后在您的 OVR Toolkit 腕表的宏选项卡中查看您的新绑定！（您可能需要重新启动 OVR Toolkit！）

<div class="embeddedVideo">
   <video name="快速重置设置概览视频" autoplay muted loop playsinline>
      <source src="../assets/videos/ovrtMacro.webm" type="video/webm">
      <source src="../assets/videos/ovrtMacro.mov" type="video/quicktime">
   </video><br>
   添加快速重置绑定的示例 GIF：
</div>

## 警告

目前，SlimeVR 服务器在按下绑定的瞬间立即重置位置，这在您低头看着伸展的手臂时并不理想。不过，这可以通过一个简单的 AutoHotKey 脚本解决，直到添加一个配置选项来为这些绑定增加倒计时。将此脚本保存为扩展名为 `.ahk` 的文件。

如果您希望此脚本随 Windows 启动，右键单击它，创建快捷方式，然后将该快捷方式复制到 `C:/Users/<您的用户名>/AppData/Roaming/Microsoft/Windows/Start Menu/Programs/Startup`

```ahk
#NoEnv  ; 推荐用于性能以及与未来 AutoHotkey 版本的兼容性。
; #Warn  ; 启用警告以帮助检测常见错误。
SendMode Input  ; 推荐用于新脚本，因其卓越的速度和可靠性。
SetWorkingDir %A_ScriptDir%  ; 确保一致的工作目录。

; 重置
$^+!y::
SoundBeep
Sleep 3000
SoundBeep
SoundBeep
SoundBeep
Send, ^!+y
return

; 快速重置
$^+!u::
SoundBeep
Sleep 3000
SoundBeep
SoundBeep
Send, ^!+u
return

; 蜂鸣声仅用于额外反馈，可以安全移除。
```

## 备注

- 如果您重置了游玩空间（例如长按 Oculus 按钮），您需要执行[追踪器重置](#重置追踪器)。
- OpenVR Advanced Settings 的按键绑定在某些语言中可能无法正常工作。如果遇到这种情况，请将系统语言设置为英语后启动 SteamVR。
- SlimeVR Server 使用 [Java 17](https://adoptium.net/releases.html?variant=openjdk17&jvmVariant=hotspot)。
- 如果您需要 SlimeVR Steam 驱动程序，可以在[此处](https://github.com/SlimeVR/SlimeVR-OpenVR-Driver/releases/latest/download/slimevr-openvr-driver-win64.zip)找到。

*由 Eiren 创建，由 adigyran、calliepepper、smeltie、emojikage 和 nullstalgia 编辑，由 calliepepper 设计样式。视频由 zrock35 制作。OVRT GIF 由 nullstalgia 制作。*
