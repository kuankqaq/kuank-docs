# 安装 OpenVR 插件

为了使 SlimeVR 能够与 SteamVR 通信，您需要将 OpenVR 驱动安装到您的 Steam 安装目录中。在 Windows 上，这会通过 SlimeVR 的安装程序自动完成。在 Linux 上，需要手动完成。

如果您不打算将 SlimeVR 与 SteamVR 一起使用，可以跳过此部分。

### 1. 下载

[最新的 OpenVR 插件可在此处下载](https://github.com/SlimeVR/SlimeVR-OpenVR-Driver/releases/latest/download/slimevr-openvr-driver-x64-linux.zip)，或者从[最新的 SlimeVR-OpenVR-Driver 发布页面](https://github.com/SlimeVR/SlimeVR-OpenVR-Driver/releases/)下载 `slimevr-openvr-driver-x64-linux.zip`。

### 2. 确定目标目录

然后您需要确定系统上 Steam 安装的根目录。在大多数情况下，它应位于 `~/.steam/steam/`。

### 3. 解压并安装

解压您在步骤 1 中下载的存档。这将在一级 `slimevr` 文件夹内提供一组文件和文件夹。

然后运行 `<steam 路径>/steamapps/common/SteamVR/bin/vrpathreg.sh adddriver /path/to/slimevr`，将 `<steam 路径>` 替换为您的 Steam 安装路径，将 `/path/to/slimevr` 替换为解压后的 `slimevr` 文件夹的完整路径。

您需要重新启动 SteamVR 才能使更改生效，不过在您设置好 SlimeVR 追踪器之前，可能不会注意到任何变化。

### 4. 设置 SteamVR 启动参数

SteamVR 需要一个启动参数以允许 SlimeVR 驱动程序连接到服务器。
要设置启动参数，打开 Steam，右键单击库中的 SteamVR，选择"属性"，您应该会看到一个可以输入启动参数的字段。
在大多数情况下，启动参数应为：`PRESSURE_VESSEL_FILESYSTEMS_RW="$XDG_RUNTIME_DIR/SlimeVRDriver" %command%`。如果您已经设置了其他启动参数，可能需要对此进行调整。

# 安装 Java

SlimeVR Server 依赖 Java 17，因此您需要在系统上安装 SlimeVR 可以访问的 Java。

### 选项 1：全局安装 Java

设置 Java 最简单直接的方法是通过您的发行版的包管理器安装。具体的包名称因发行版而异，但很可能列为 "`openjdk`"，您很可能需要 `jre`（不过 `jdk` 也可以正常工作）。

Ubuntu：

```
sudo apt install openjdk-17-jre
```

Arch Linux：

```
sudo pacman -S jre17-openjdk
```

安装完成后，SlimeVR AppImage 应自动检测并使用此版本的 Java 来运行内部服务器。

### 选项 2：便携版 Java

另一种方法是下载并解压便携版 Java 运行时。

#### 1. 下载 Java 17 JRE 存档

您可以点击此按钮直接下载最新的 Adoptium JRE 存档：

<script>
async function downloadLatestAdoptium() {
  const latestFiles = await(await fetch('https://api.adoptium.net/v3/assets/latest/17/hotspot?os=linux&architecture=x64&image_type=jre')).json();

  if (!latestFiles || (Array.isArray(latestFiles) && !latestFiles.length)) {
    console.log('无法找到任何发布版本 :c');
    return;
  }

  let latestFile = (Array.isArray(latestFiles) ? latestFiles[0] : latestFiles).binary.package.link;
  console.log('找到最新的 Adoptium 版本:', latestFile);

  window.open(latestFile);
}
</script>

<button onclick="downloadLatestAdoptium()">下载最新的 Adoptium 17 LTS</button>

或者您也可以从此发布页面自行下载：

<https://adoptium.net/temurin/releases/?version=17>

#### 2. 解压并重命名

1. 解压下载的存档（例如 `OpenJDK17U-jre_x64_linux_hotspot_17.0.5_8.tar.gz`），得到一个类似 `jdk-17.0.5+8-jre` 的文件夹。
2. 将解压后的文件夹（例如 `jdk-17.0.5+8-jre`）重命名为 `jre`，使目录结构看起来类似于 `/jre/bin/java`。

#### 3. 与 SlimeVR 捆绑

为了让 SlimeVR 找到便携版 Java，您需要将其与 AppImage 放在同一目录中。在使用本指南"运行 SlimeVR"部分的一体化 AppImage 时，您的文件夹结构应如下所示：

```
父目录
    |- /jre/bin/java
    |- /SlimeVR-amd64.appimage
```

# 运行 SlimeVR

在 Linux（桌面环境）上运行 SlimeVR 的推荐方式是使用为您的发行版构建的包。这包含了服务器、GUI 和 udev 规则（串行控制台所需），全部整合在一起。配置和日志将存储在 `~/.config/dev.slimevr.SlimeVR/`。

### Arch Linux

从 AUR 安装 [`slimevr-beta-bin`](https://aur.archlinux.org/packages/slimevr-beta-bin)。

### Fedora

从 GitHub 上的最新服务器发布版本安装 [.rpm 包](https://github.com/SlimeVR/SlimeVR-Server/releases/latest/download/SlimeVR-amd64.rpm)。

### Debian/Ubuntu/Mint

从 GitHub 上的最新服务器发布版本安装 [.deb 包](https://github.com/SlimeVR/SlimeVR-Server/releases/latest/download/SlimeVR-amd64.deb)。

### NixOS

将 [`slimevr`](https://search.nixos.org/packages?channel=unstable&show=slimevr&query=slimevr) 包添加到您的系统配置中的 `environment.systemPackages`。

### AppImage（适用于其他发行版）

最新的 AppImage 可以从 [GitHub 发布页面](https://github.com/SlimeVR/SlimeVR-Server/releases/latest/download/SlimeVR-amd64.appimage) 下载。如果可用，应优先选择为您的发行版构建的包，因为 AppImage 不包含 udev 规则。
然后您只需执行 AppImage 即可启动 SlimeVR。

# 串行控制台

如果您不是使用 SlimeVR 的发行版包，您需要授予您的用户帐户访问 PlatformIO 设备的权限。如果没有正确的权限，在 SlimeVR 追踪器通过 USB 连接后，串行控制台将持续显示"连接串口丢失，正在重新连接..."。

获得权限的推荐方式是安装 PlatformIO 的 udev 规则。可以按照此页面上的说明进行操作：<https://docs.platformio.org/en/latest/core/installation/udev-rules.html>

# 防火墙规则

在 Linux 上，SlimeVR 不会自动添加任何防火墙规则。如果您安装了防火墙，您需要手动添加规则。

您需要开放以下端口：
* `35903/udp`
* `6969/udp`
* `21110/tcp`
* `8266/udp`

来源：[firewall.bat](https://github.com/SlimeVR/SlimeVR-Server/blob/main/server/core/resources/firewall.bat)

# 传统设置

如果上述安装方法适用于您，则可以忽略此部分的所有内容。

如果由于某种原因上述设置不适合您，您可能需要手动获取并运行 SlimeVR 组件。

## SlimeVR Server

您可以通过此链接下载最新的 `slimevr.jar` 文件：

<https://github.com/SlimeVR/SlimeVR-Server/releases/latest/download/slimevr.jar>

## SlimeVR GUI

您可以从此处下载最新的 GUI：

<https://github.com/SlimeVR/SlimeVR-Server/actions/workflows/build-gui.yml?query=branch%3Amain+is%3Asuccess>

### 1. 打开最新的工作流运行

点击最新工作流运行的标题，这只是一个示例；具体哪个在最顶端会变化。

### 2. 下载所需的构建工件

打开工作流运行后，您可以找到构建工件的列表。最简单的是使用 AppImage 构建，因为它包含所有必需的依赖项，并且非常容易运行。

您必须登录 GitHub 帐户才能下载构建工件。

### 3. 解压 GUI AppImage/Deb

下载文件（例如 `SlimeVR-GUI-AppImage.zip`）后，解压以获取类似 `slimevr-ui_0.0.0_amd64.AppImage` 的文件。

## 设置安装文件夹

为了最方便地使用程序，您需要以特定方式组织文件。

1. 创建一个新文件夹来存放安装文件，名称自定义（例如 `SlimeVR Server`）。
2. 将您下载的 SlimeVR Server、SlimeVR GUI 以及可选的 Java JRE 组件放入您创建的文件夹中。

最终目录结构示例：

```
/SlimeVR Server/
    |- /jre/bin/java  （如果使用便携版 Java）
    |- /slimevr.jar
    |- /slimevr-ui_0.0.0_amd64.AppImage
```

## 运行程序

一切设置完成后，您只需执行 AppImage，它应自动运行所有其他组件。

注意：仅在 Debian 和 Ubuntu 上测试过，如果您使用 Arch，请在 SlimeVR Discord 服务器中联系 lordbagel42。

*由 butterscotch.v 创建。*
