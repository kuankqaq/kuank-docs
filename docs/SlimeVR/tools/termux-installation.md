# Termux 设置

**不再推荐本指南。请参阅[移动端设置](mobile-installation.md)了解在独立设备上运行 SlimeVR 的更新方法。**

本指南将帮助您安装 Termux，一个用于 Android 的 Linux"模拟器"，用于 SlimeVR。Quest 2 恰好运行 Android，因此您可以使用 Termux 在其上运行 SlimeVR 服务器。

注意：目前 Joy-Con 仍需要 PC 和 [SlimeVR Wrangler](https://github.com/carl-anders/slimevr-wrangler)。

# 安装 - QUEST 2

1. 从此处下载 Termux（Quest 1/2 为 arm64）：[https://github.com/termux/termux-app/releases](https://github.com/termux/termux-app/releases)

2. 使用 Sidequest、ADB 或已安装的文件管理器安装 .APK 文件。

3. 打开 Termux，并运行以下命令：

```
bash <(curl https://raw.githubusercontent.com/SlimeVR/SlimeVR-Termux-Installer/main/install.sh)
```

4. 如果浏览器没有自动打开，请在运行服务器的设备上访问 [https://slimevr-gui.bscotch.ca/](https://slimevr-gui.bscotch.ca/)。

## 如果关闭后想要再次启动服务器，**不要**再次运行设置命令。请运行：

```
./start.sh
```

# 安装 - ANDROID 手机

1. 在手机上启用开发者模式。您可以通过打开设置，进入关于手机，找到"版本号"并连续点击七次来完成此操作。

2. 从此处下载 Termux（大多数手机为 arm64，您可以搜索确认您的型号）：[https://github.com/termux/termux-app/releases](https://github.com/termux/termux-app/releases)
   **不要从 Google Play 安装。**

3. 点击 APK 文件，并允许安装。

4. 打开 Termux，并运行以下命令：

```
bash <(curl https://raw.githubusercontent.com/SlimeVR/SlimeVR-Termux-Installer/main/install.sh)
```

5. 如果浏览器没有自动打开，请在运行服务器的设备上访问 [https://slimevr-gui.bscotch.ca/](https://slimevr-gui.bscotch.ca/)。

## 如果关闭后想要再次启动服务器，**不要**再次运行设置命令。请运行：

```
./start.sh
```

# 更新

在 Android 和 Quest 上，您只需启动它即可完成更新，它会自动检查更新。

# 远程 GUI 访问

第一步是在您使用的浏览器上启用此功能：[https://www.damirscorner.com/blog/posts/20210528-AllowingInsecureWebsocketConnections.html](https://www.damirscorner.com/blog/posts/20210528-AllowingInsecureWebsocketConnections.html)
为 https://slimevr-gui.bscotch.ca/ 启用它。
完成此操作后，您可以访问 https://slimevr-gui.bscotch.ca/?ip=[QUEST 或手机 IP]&port=21110 来访问该站点。将 [QUEST 或手机 IP] 替换为您 Quest 或手机的 IP 地址，不要带方括号。

*功劳归于 butterscotch.v 实现了这一切，以及 lordbagel42 提供的文档、想法和动力。*
