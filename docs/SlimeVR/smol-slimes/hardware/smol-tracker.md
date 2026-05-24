<link rel="stylesheet" href="../assets/css/smol-slimes.css">

# 🏃 Smol 追踪器

开始之前，请先确定[您可能需要多少个追踪器](../../user-guide/slimevr101.md#how-many-trackers-do-you-need)。

追踪器需要配备电池和惯性测量单元（IMU）。磁力计是可选的。\
建议但非必需添加按钮和滑动开关。按钮可用于控制追踪器，滑动开关可用于物理断开追踪器的电池连接。

## 目录

- TOC
  {:toc}

## 原理图

<form id="schematicForm">
  <fieldset class="form-field-group">
    <legend>原理图：</legend>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="checkbox" name="isStacked" checked="checked" />
        堆叠式原理图
        <sup>✅ 推荐</sup>
      </div>
      <span class="form-field-description">
        IMU 放置在 ProMicro 上方，无需额外 PCB。
      </span>
    </label>
  </fieldset>
  <fieldset class="form-field-group">
    <legend>IMU：</legend>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="radio" name="IMU" value="ICM-45686" checked="checked" />
        ICM-45686
        <sup>
          <a href="../../diy/imu-comparison.md#icm-45686" target="_blank"> [更多] </a>
        </sup>
      </div>
      <span class="form-field-description">
        价格更高，精度更高。
      </span>
    </label>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="radio" name="IMU" value="LSM6DSV" /> LSM6DSV
        <sup>
          <a href="../../diy/imu-comparison.md#lsm6dsv" target="_blank"> [更多] </a>
        </sup>
      </div>
    </label>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="radio" name="IMU" value="LSM6DSR" /> LSM6DSR
        <sup>
          <a href="../../diy/imu-comparison.md#lsm6dsr" target="_blank">[更多]</a>
        </sup>
      </div>
      <span class="form-field-description">
        价格是 ICM-45686 的一半，漂移略大。
      </span>
    </label>
  </fieldset>
  <fieldset class="form-field-group">
    <legend>通信协议：</legend>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="radio" name="Protocol" value="SPI" checked="checked" />
        SPI
        <sup>✅ 推荐</sup>
      </div>
      <span class="form-field-description">
        功耗更低，性能更高。暂不支持磁力计。
      </span>
    </label>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="radio" name="Protocol" value="I2C" /> I2C
      </div>
      <span class="form-field-description">
        支持磁力计。
      </span>
    </label>
  </fieldset>
  <fieldset class="form-field-group">
    <legend>额外选项：</legend>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="checkbox" name="HasUserButton" checked="checked" />
        用户按钮
        <sup>✅ 推荐</sup>
      </div>
      <span class="form-field-description">
        可编程用户按钮，主要用于深度睡眠。
      </span>
    </label>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="checkbox" name="hasResetButton" />
        复位按钮
      </div>
      <span class="form-field-description">
        堆叠式 Smol 上不可用。
      </span>
    </label>
    <label class="form-field-input-container">
      <div class="form-field-input">
        <input type="checkbox" name="hasAntenna" />
        天线
        <sup>✅ 推荐</sup>
      </div>
      <span class="form-field-description">
        通过添加短 wire 到天线来改善范围
        <sup>
          <a href="./smol-receiver.html#option-2-wire-antenna-mod" target="_blank">[更多]</a>
        </sup>
        或 Wi-Fi 天线（用于接收器）
        <sup>
          <a href="./smol-receiver.html#option-3-wi-fi-antenna-mod" target="_blank">[更多]</a>
        </sup>
      </span>
    </label>
  </fieldset>
</form>

<div
  id="schema-canvas"
  class="chip"
></div>

!!! warning
    即使追踪器未启用睡眠功能，INT 引脚也是必需的。

## 追踪器部件

### 📻 微控制器板

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>板卡</th>
        <th>描述</th>
        <th>购买渠道</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <span id="ProMicro"> ProMicro nRF52840 </span>
        </td>
        <td>
          <strong>nice!nano</strong> 板的克隆版。整体最便宜的选项。 <br />
          信号强度可通过天线改装来改善。
        </td>
        <td>
          在 AliExpress 上以 <code>compatible with nice!nano</code>、<code>SuperMini</code> 或 <code>Pro Micro</code> 品牌提供。
          <ul>
            <li><a href="https://pl.aliexpress.com/item/1005007738886550.html">AliExpress TENSTAR 2 个装</a></li>
          </ul>
        </td>
      </tr>
      <tr>
        <td>
          <span id="XIAO"> Seeed Studio XIAO nRF52840 </span>
        </td>
        <td>紧凑型板卡。</td>
        <td>
          <ul>
            <li><a href="https://www.seeedstudio.com/Seeed-XIAO-BLE-nRF52840-p-5201.html">制造商列表</a></li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>

### 🧭 惯性测量单元

部分支持的传感器模块在 [IMU 对比页面](../../diy/imu-comparison.md) 中有描述。

- BMI270
- ICM-42688-P
- ICM-42688-V
- ICM-45686
- ISM330BX
- ISM330DHCX
- ISM330DLC
- LSM6DSL
- LSM6DSM
- LSM6DSO
- LSM6DSR
- LSM6DSV
- LSM6DSV16B

### 🧲 磁力计

- AK09940
- <div class="tooltip-text-container">BMM150
   <span class="tooltip-text">传感器驱动程序未经测试。</span>
  </div>
- <div class="tooltip-text-container">BMM350
   <span class="tooltip-text">传感器驱动程序未经测试。</span>
  </div>
- IIS2MDC
- IST8306
- IST8308
- LIS2MDL
- <div class="tooltip-text-container">LIS3MDL
   <span class="tooltip-text">传感器驱动程序未经测试。</span>
  </div>
- MMC5983MA
- QMC6309

### 🟩 带 IMU 和磁力计的传感器模块

##### IMU + 磁力计模块

<div class="table-wrapper">
    <table>
        <thead>
            <tr>
                <th>IMU + 磁力计</th>
                <th>产品页面</th>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>
                    <a href="../../diy/imu-comparison.md#icm-45686">ICM-45686</a> + QMC6309
                </td>
                <td>
                    <a href="https://shop.slimevr.dev/products/slimevr-mumo-breakout-module-v1-icm-45686-qmc6309">shop.slimevr.dev</a>
                </td>
            </tr>
            <tr>
                <td><a href="../../diy/imu-comparison.md#lsm6dsr">LSM6DSR</a> + QMC6309</td>
                <td>
                    <a href="https://moffshop.deyta.de/products/lsm6dsr">moffshop.deyta.de</a>
                </td>
            </tr>
            <tr>
                <td>
                    Chrysalis <a href="../../diy/imu-comparison.md#icm-45686">ICM-45686</a> + QMC6309
                </td>
                <td>
                    <a href="https://nekumori.pink/products/chysalis-v1_3">nekumori.pink</a>
                </td>
            </tr>
        </tbody>
    </table>
</div>

### 🖲️ 按钮

按钮和瞬时开关用于控制追踪器。此按钮的功能——复位、校准、配对、深度睡眠和进入 DFU 模式——取决于按动组合次数。追踪器可以配备复位按钮、用户指定按钮（SW0）或两者兼有。

复位按钮设计用于支持所有功能。如果定义了用户指定按钮（SW0），将优先使用该按钮。

如果没有按钮，可以使用镊子短接引脚以进行初始追踪器设置。

### 🕹️ 开关

滑动开关可用于物理断开电池连接。某些板的待机功耗较高，需要开关。

如果未使用开关，可以通过长按用户指定按钮（SW0）使追踪器进入深度睡眠模式。

### 🔋 电池

安全充电倍率（C）与其额定容量（mAh）相关。100mAh 电池以 100mA 充电为 1C，200mAh 电池以 100mA 充电为 0.5C。建议以接近 0.5C 的较低倍率充电，以减少电池压力并延长使用寿命。

| 板卡                      | 默认充电速率 | 最小电池容量 | 推荐电池容量 |
| -------------------------- | ------------ | ------------ | ------------ |
| Seeed Studio XIAO nRF52840 | 50mA         | 50mAh        | 80-300mAh    |
| ProMicro nRF52840          | 100mA        | 100mAh       | 180-300mAh   |

### 📶 用于 Wire 天线改装的铜线

便宜且简单的方法来改善信号强度。

将 31.2 mm 的 wire 连接到天线引脚，形成基本单极天线。更长也可以。

焊点位置请参考 <a href="#schematics">Smol 原理图 -> 天线（额外选项）</a>。

注意：
- 必须绝缘以避免与其他组件短路。
- 品牌 wire 比实心线略差，但差别不大。
- wire 可以从以太网线缆中获取。

### 📏 金手指胶带（仅限堆叠式）

!!! warning
    制作堆叠式 Smol 追踪器时，请勿跳过此步骤。

将其放置在板卡和 IMU 之间，以及 IMU 背面，以防止短路并保护组件。

### 🧤 绑带

追踪器需要绑带或固定方案才能实际使用。

社区设计的绑带方案可在 [Smol 社区绑带](./smol-slimes-community-straps.md) 页面上找到。

### 📦 外壳

外壳可保护组件，提高耐用性，并使追踪器更易于固定或佩戴。

社区设计的外壳可在 [Smol 社区构建](./smol-slimes-community-builds.md) 页面上找到。

---

*由 Shine Bright ✨、[Depact](https://github.com/Depact)、[Aed](https://github.com/Aed-1) 和 [Seneral](https://github.com/Seneral) 创建，图片由 [Meia](https://github.com/kounocom) 和 [Firmata](https://github.com/Firmatorenio) 提供*

<link rel="stylesheet" href="../assets/css/smol-slimes.css" />
<link rel="stylesheet" href="../assets/css/smol-tracker-schematics.css" />
<script src="../assets/js/smol-tracker-schematics.js"></script>
