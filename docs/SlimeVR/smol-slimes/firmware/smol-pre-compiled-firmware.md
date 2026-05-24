<link rel="stylesheet" href="../assets/css/smol-slimes.css">

# 默认引脚的预编译固件

!!! note
    如果您不需要自定义配置或引脚定义，这是获取固件的推荐方法。

## 目录

- TOC
  {:toc}

## 所需工具

如果您使用预编译固件，只需要以下工具：
* <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop">nRF Connect for Desktop</a>（编程器）仅用于刷写 Nordic 或 eByte 接收器
* <a href="https://www.nordicsemi.com/Products/Development-tools/nRF-Connect-for-Desktop">nRF Connect for Desktop</a>（串行终端）用于向您的接收器/追踪器发送命令，[查看替代方案](smol-pairing-and-calibration.md#accessing-the-serial-console)
* 或 [SmolSlimeConfigurator](SmolSlimeConfigurator.md)，一款适用于您的 Smol Slimes 的多合一编程和配置工具。
* <a href="https://slimevr.dev/download">SlimeVR Server</a>
    * 0.13.2 或更高版本


## 最新构建的引导加载程序（自动化）

#### 💿 Adafruit 引导加载程序

| 设备 | UF2 | HEX |
| ------------------ | ---- | ---- |
| ProMicro | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimenrf_promicro_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimenrf_promicro_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |
| XIAO | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimenrf_xiao_sense_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimenrf_xiao_sense_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |
| R3 | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimenrf_tracker_r3_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimenrf_tracker_r3_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |
| Butterfly P1 | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimevr_mini_p1_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimevr_mini_p1_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |
| Butterfly P2 | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimevr_mini_p2_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimevr_mini_p2_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |
| Butterfly P3, R6 | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimevr_mini_p3r6_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimevr_mini_p3r6_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |
| Butterfly P3, R7 | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/update-slimevr_mini_p3r7_bootloader-0.9.2-SlimeVR.7_nosd.uf2) | [链接](https://github.com/SlimeVR/Adafruit_nRF52_Bootloader/releases/download/0.9.2-SlimeVR.7/slimevr_mini_p3r7_bootloader-0.9.2-SlimeVR.7_s140_7.3.0.hex) |

## 最新构建的固件（自动化）

### 📡 接收器

| 设备 | 下载 |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Nordic/eByte | [链接](https://github.com/Shine-Bright-Meow/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Nordic_eByte_Dongle_Receiver.hex) |
| Holyiot | [链接](https://github.com/Shine-Bright-Meow/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Holyiot_Dongle_Receiver.hex) |
| ProMicro | [链接](https://github.com/Shine-Bright-Meow/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_ProMicro_Receiver.uf2) |
| XIAO | [链接](https://github.com/Shine-Bright-Meow/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_XIAO_Receiver.uf2) |

### 🏃 追踪器

#### 追踪器固件选项说明

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>选项</th>
        <th>值</th>
        <th>含义</th>
        <th>推荐</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><strong>协议</strong></td>
        <td>SPI/I2C</td>
        <td>
          微控制器与 IMU 传感器之间的通信方式。
          <ul>
            <li><strong>SPI：</strong>通常更快、更可靠。</li>
            <li><strong>I2C：</strong>效率较低，强烈不推荐。</li>
          </ul>
        </td>
        <td>SPI</td>
      </tr>
      <tr>
        <td><strong>时钟</strong></td>
        <td>开/关</td>
        <td>
          连接的 IMU 是否使用外部时钟。
            <ul>
               <li>✅ = 存在外部时钟。</li>
               <li>✖️ = 仅使用内部时钟。</li>
            </ul>
        </td>
        <td>✅（当硬件支持外部时钟时）</td>
      </tr>
      <tr>
        <td><strong>睡眠 (WOM)</strong></td>
        <td>✅/✖️</td>
        <td>
            WOM 代表 Wake-On-Motion（动作唤醒）模式。
            <ul>
               <li>✅ = 追踪器可以睡眠并在动作时唤醒。延长电池寿命。</li>
               <li>✖️ = 始终活跃。漂移更少，追踪更好，以电池寿命为代价。</li>
            </ul>
            在两种情况下，追踪器在失去与接收器的连接 5 分钟后都会进入深度睡眠。
         </td>
        <td>✖️（除非电池寿命是最高优先级）</td>
      </tr>
      <tr>
        <td><strong>SW0 已启用（按钮）</strong></td>
        <td>N/A</td>
        <td>
         <p>编译时包含按钮支持的固件。</p>
         <p>允许物理按钮输入来控制追踪器。</p>
        </td>
        <td>如果您的硬件有按钮。</td>
      </tr>
      <tr>
        <td><strong>SW0 已禁用（无按钮）</strong></td>
        <td>N/A</td>
        <td>
         <p>编译时不包含按钮支持的固件。</p>
         <p>未分配物理按钮按下功能。</p>
        </td>
        <td>非标准选项。</td>
      </tr>
    </tbody>
  </table>
</div>

#### 🥪 堆叠式

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>设备</th>
        <th>协议</th>
        <th>时钟 (ICM)</th>
        <th>
          睡眠
          <span class="tooltip-text-container">
            (WOM)
            <span class="tooltip-text"> 动作唤醒 </span>
          </span>
        </th>
        <th>
            SW0 已禁用
            <br/>
            （无按钮）
        </th>
        <th>
            SW0 已启用
            <br/>
            （有按钮）
        </th>
      </tr>
    </thead>
    <tbody>
      <!-- ProMicro，堆叠式，有 CLK -->
      <tr>
        <td rowspan="4">ProMicro</td>
        <td rowspan="2">SPI</td>
        <td rowspan="4">✅</td>
        <td>✅</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SPI_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
      <tr>
        <td>✖️</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SPI_StackedSmol.uf2" target="_blank">链接</a> <sup style="font-size:0.6em">✅ 推荐</sup>
        </td>
      </tr>
      <tr>
        <td rowspan="2">I2C</td>
        <td>✅</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_I2C_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
      <tr>
        <td>✖️</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_I2C_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
    </tbody>
    <tbody>
      <!-- ProMicro，堆叠式，无 CLK -->
      <tr>
        <td rowspan="4">ProMicro</td>
        <td rowspan="2">SPI</td>
        <td rowspan="4">✖️</td>
        <td>✅</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoCLK_SPI_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
      <tr>
        <td>✖️</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoCLK_NoSleep_SPI_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
      <tr>
        <td rowspan="2">I2C</td>
        <td>✅</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoCLK_I2C_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
      <tr>
        <td>✖️</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoCLK_NoSleep_I2C_StackedSmol.uf2" target="_blank">链接</a>
        </td>
      </tr>
    </tbody>
  </table>
</div>

#### 普通（非堆叠式）

<div class="table-wrapper">
   <table>
      <thead>
         <tr>
            <th>设备</th>
            <th>协议</th>
            <th>时钟 (ICM)</th>
            <th>
               睡眠
               <span class="tooltip-text-container">
               (WOM)
               <span class="tooltip-text"> 动作唤醒 </span>
               </span>
            </th>
            <th>
               SW0 已禁用
               <br/>
               （无按钮）
            </th>
            <th>
               SW0 已启用
               <br/>
               （有按钮）
            </th>
         </tr>
      </thead>
      <!-- ProMicro, SPI, 非堆叠 -->
      <tr>
         <td rowspan="8">ProMicro</td>
         <td rowspan="4">SPI</td>
         <td rowspan="2">✖️</td>
         <td>✅</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SPI_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_SPI_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <tr>
         <!-- ProMicro, SPI, 非堆叠, 无睡眠 -->
         <td>✖️</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SPI_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_NoSleep_SPI_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <tr>
         <!-- ProMicro, SPI, 非堆叠, 有 CLK，睡眠 -->
         <td rowspan="2">✅</td>
         <td>✅</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_CLK_SPI_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_CLK_SPI_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <tr>
         <!-- ProMicro, SPI, 非堆叠, 有 CLK, 无睡眠 -->
         <td>✖️</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleepCLK_SPI_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_NoSleepCLK_SPI_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <!-- ProMicro, I2C, 非堆叠 -->
      <tr>
         <td rowspan="4">I2C</td>
         <td rowspan="2">✖️</td>
         <td>✅</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_I2C_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_I2C_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <tr>
         <td>✖️</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_I2C_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_NoSleep_I2C_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <tr>
         <td rowspan="2">✅</td>
         <td>✅</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_CLK_I2C_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_CLK_I2C_ProMicro.uf2">链接</a>
         </td>
      </tr>
      <tr>
         <td>✖️</td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleepCLK_I2C_ProMicro.uf2">链接</a>
         </td>
         <td>
            <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_NoSleepCLK_I2C_ProMicro.uf2">链接</a>
         </td>
      </tr>
      </tbody>
      <tbody>
         <!-- XIAO -->
         <tr>
            <td rowspan="4">XIAO</td>
            <td rowspan="4">I2C/SPI</td>
            <td rowspan="2">✖️</td>
            <td>✅</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_XIAO.uf2">链接</a>
            </td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_XIAO.uf2">链接</a>
            </td>
         </tr>
         <tr>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_XIAO.uf2">链接</a>
            </td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_NoSleep_XIAO.uf2">链接</a>
            </td>
         </tr>
         <tr>
            <td rowspan="2">✅</td>
            <td>✅</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_CLK_XIAO.uf2">链接</a>
            </td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_CLK_XIAO.uf2">链接</a>
            </td>
         </tr>
         <tr>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleepCLK_XIAO.uf2">链接</a>
            </td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SW0_NoSleepCLK_XIAO.uf2">链接</a>
            </td>
         </tr>
      </tbody>
      <tbody>
         <!-- R3 -->
         <tr>
            <td rowspan="2">R3</td>
            <td rowspan="2">I2C</td>
            <td rowspan="2">✅</td>
            <td>✅</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_R3.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
         <tr>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_R3.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
      </tbody>
      <tbody>
         <!-- Butterfly (P1) -->
         <tr>
            <td rowspan="2">Butterfly (P1)</td>
            <td rowspan="2">I2C</td>
            <td rowspan="2">✅</td>
            <td>✅</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SlimevrMini.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
         <tr>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SlimevrMini.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
      </tbody>
      <tbody>
         <!-- Butterfly (P2) -->
         <tr>
            <td rowspan="2">Butterfly (P2)</td>
            <td rowspan="2">I2C</td>
            <td rowspan="2">✅</td>
            <td>✅</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_SlimevrMini2.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
         <tr>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SlimevrMini2.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
      </tbody>
      <tbody>
         <!-- Butterfly (P3, R6) -->
         <tr>
            <td>Butterfly (P3, R6)</td>
            <td>I2C</td>
            <td>✅</td>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SlimevrMini3_R6.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
      </tbody>
      <tbody>
         <!-- Butterfly (P3, R7) -->
         <tr>
            <td>Butterfly (P3, R7)</td>
            <td>I2C</td>
            <td>✅</td>
            <td>✖️</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SlimevrMini3_R7.uf2">链接</a>
            </td>
            <td>N/A</td>
         </tr>
         <!-- Butterfly (P4, R8) -->
         <tr>
            <td>Butterfly (P4, R8)</td>
            <td>SPI</td>
            <td>✅</td>
            <td>✖️</td>
            <td>N/A</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SlimevrMini4.uf2">链接</a>
            </td>
         </tr>
         <!-- Butterfly (P4, R9) -->
         <tr>
            <td>Butterfly (P4, R9)</td>
            <td>SPI</td>
            <td>✅</td>
            <td>✖️</td>
            <td>N/A</td>
            <td>
               <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_SlimevrMini4R9.uf2">链接</a>
            </td>
         </tr>
      </tbody>
   </table>
</div>

#### ⚙️ PCB

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>设备</th>
        <th>协议</th>
        <th>时钟 (ICM)</th>
        <th>
          睡眠
          <span class="tooltip-text-container">
            (WOM)
            <span class="tooltip-text"> 动作唤醒 </span>
          </span>
        </th>
        <th>
            SW0 已禁用
            <br/>
            （无按钮）
        </th>
        <th>
            SW0 已启用
            <br/>
            （有按钮）
        </th>
      </tr>
    </thead>
    <tbody>
      <!-- Chrysalis -->
      <tr>
        <td rowspan="2">Chrysalis</td>
        <td rowspan="2">SPI</td>
        <td rowspan="2">✅</td>
        <td>✅</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_Chrysalis_ProMicro.uf2" target="_blank">链接</a>
        </td>
      </tr>
      <tr>
        <td>✖️</td>
        <td>N/A</td>
        <td>
          <a href="https://github.com/kounocom/SlimeNRF-Firmware-CI/releases/download/latest/SlimeNRF_Tracker_NoSleep_Chrysalis_ProMicro.uf2" target="_blank">链接</a>
        </td>
      </tr>
    </tbody>
  </table>
</div>

### 以前的固件构建

以前的构建可在此处找到：<a href="https://github.com/Shine-Bright-Meow/SlimeNRF-Firmware-CI/actions">https://github.com/Shine-Bright-Meow/SlimeNRF-Firmware-CI/actions</a>

1. 点击指定日期范围内的成功工作流运行 ✅。
2. 向下滚动到 **Artifacts**（构件）部分。
3. 下载所需的设备固件。
4. 解压 ZIP 文件。

---

*由 Shine Bright ✨、[Depact](https://github.com/Depact) 和 [Seneral](https://github.com/Seneral) 创建*
