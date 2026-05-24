<link rel="stylesheet" href="../assets/css/smol-slimes.css">

# Smol 接收器

# 目录

- TOC
  {:toc}

## 📶 接收器选项（按信号强度排序）

为确保最佳信号完整性和范围，必须使用配备高质量天线的板卡。采用 PCB 天线或外部天线的板卡通常是用作接收器的最有效选择。

<a href="#NordicDongle">Nordic Semiconductor nRF52840 Dongle</a>、<a href="#-microcontrollers-modified-into-usb-dongles">Seeed Studio XIAO nRF52840</a> 因缺少数据未被列入。

<div class="table-wrapper">
  <table class="transform-table-to-list-on-mobile">
    <thead>
      <tr>
        <th>接收器</th>
        <th>等级</th>
        <th>典型价格（美元）</th>
        <th>备注 / 最适合</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>🟢 <a href="#HolyIOT">HolyIOT-21017</a></td>
        <td data-label="等级："><span style="color:#2ecc40;font-weight:bold">优越</span></td>
        <td data-label="典型价格：">~8-18 美元</td>
        <td data-label="备注 / 最适合：">
          价格最高，性能最强。
          <br/>
          包含 RFX2401C FEM 放大器——据报告可显著提升信号强度。
        </td>
      </tr>
      <tr>
        <td>🟠 <a href="#option-3-wi-fi-antenna-mod">ProMicro nRF52840（Wi‑Fi 天线改装版）</a></td>
        <td data-label="等级："><span style="color:#27ae60;font-weight:bold">经济实惠</span></td>
        <td data-label="典型价格：">~7 美元</td>
        <td data-label="备注 / 最适合：">改装 Wi‑Fi 天线后性价比最佳。</td>
      </tr>
      <tr>
        <td>🟠 <a href="#option-2-wire-antenna-mod">ProMicro nRF52840（ wire 天线改装版）</a></td>
        <td data-label="等级："><span style="color:#27ae60;font-weight:bold">经济实惠</span></td>
        <td data-label="典型价格：">~6 美元</td>
        <td data-label="备注 / 最适合：">简单的 31.2 mm wire 单极天线；成本低且易于制作；范围提升适中。</td>
      </tr>
      <tr>
        <td>🟠 <a href="#eByteDongle">eByte 接收器（E104-BT5040U）</a></td>
        <td data-label="等级："><span style="color:#e67e22;font-weight:bold">有限</span></td>
        <td data-label="典型价格：">Alibaba 上最少 2 个装约 6.25 美元</td>
        <td data-label="备注 / 最适合：">最便宜的 PCB 天线接收器。信号在超过约 3 米后会衰减，尤其是在被身体部位遮挡时。</td>
      </tr>
      <tr>
        <td>🚫 <a href="#option-1-unmodified-board">ProMicro nRF52840（未改装）</a></td>
        <td data-label="等级："><span style="color:#e74c3c;font-weight:bold">避免</span></td>
        <td data-label="典型价格：">~2-4 美元</td>
        <td data-label="备注 / 最适合：">未改装的板卡；与追踪器相同。不建议使用，因为改装天线更好。</td>
      </tr>
    </tbody>
  </table>
</div>

## 📡 USB 接收器

这些接收器配备了相对优化的 PCB 天线。为在受限环境中改善信号完整性，请考虑使用 USB 延长线。

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>接收器</th>
        <th>描述</th>
        <th>链接</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <span id="eByteDongle">🟠 eByte 接收器（E104-BT5040U）</span>
        </td>
        <td>
          带有 PCB 天线的最便宜选项。<br />
          - <strong>E104-BT5040U</strong> 是应使用的正确型号。它与 Nordic Semiconductor nRF52840 Dongle 完全兼容。<br />
          - <strong>E104-BT5040UA</strong> 不兼容。它只能捕获 BLE4.2 和 BLE5.0 协议包。
        </td>
        <td>
          <ul>
            <li>
              <a href="https://www.cdebyte.com/products/E104-BT5040U">制造商页面</a>
            </li>
            <li>
              <a href="https://www.alibaba.com/product-detail/Ebyte-ODM-E104-BT5040U-nRF52840-BLE4_1600579144016.html?spm=a2756.trade-list-buyer.0.0.535476e9B4p1qV">Alibaba</a>
            </li>
          </ul>
        </td>
      </tr>
      <tr>
        <td>
          <span id="NordicDongle">Nordic Semiconductor nRF52840 Dongle（PCA10059）</span>
        </td>
        <td>官方 Nordic 开发硬件。</td>
        <td>
          <ul>
            <li><a href="https://www.nordicsemi.com/Products/Development-hardware/nRF52840-Dongle">制造商页面</a></li>
            <li><a href="https://www.digikey.com/en/products/detail/nordic-semiconductor-asa/NRF52840-DONGLE/9491124">Digikey</a></li>
            <li><a href="https://eu.mouser.com/ProductDetail/Nordic-Semiconductor/nRF52840-Dongle?qs=gTYE2QTfZfTbdrOaMHWEZg%3D%3D">Mouser</a></li>
          </ul>
        </td>
      </tr>
      <tr>
        <td>
          <span id="HolyIOT">🟢 HolyIOT-21017 又名 HOLYIOT-21017-nRF52840</span>
        </td>
        <td>
          具有 FEM（前端模块），具体为 <strong>RFX2401C</strong> 射频增强器。
          目前被认为是性能最高的选项。
        </td>
        <td>
          <ul>
            <li><a href="http://www.holyiot.com/eacp_view.asp?id=336">制造商页面</a></li>
            <li><a href="https://www.aliexpress.com/item/1005004673179004.html">AliExpress</a></li>
            <li><a href="https://holyiot.en.alibaba.com/search/product?SearchText=HOLYIOT-21017-nRF52840">Alibaba</a></li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>

## 📡 改装为 USB 接收器的微控制器

#### 🚫 选项 1：未改装的板卡
!!! warning
    不推荐，因为升级到改装版非常简单。

由 <a href="#-microcontrollers-modified-into-usb-dongles">ProMicro nRF52840</a> 或 <a href="#-microcontrollers-modified-into-usb-dongles">Seeed Studio XIAO nRF52840</a> 组成。

#### 🟠 选项 2：Wire 天线改装

由 <a href="#-microcontrollers-modified-into-usb-dongles">ProMicro nRF52840</a> 或 <a href="#-microcontrollers-modified-into-usb-dongles">Seeed Studio XIAO nRF52840</a> 组成，在天线引脚上连接一根 31.2 mm 的 wire 形成基本单极天线。

焊点位置请参考 <a href="./smol-tracker.md#schematics">Smol 原理图 -> 天线（额外选项）</a>。

##### Wire 选项

- 实心或绞合铜 wire（例如 23-26 AWG）。
- 从以太网线缆中回收的 wire。

#### 🟠 选项 3：Wi-Fi 天线改装

由 <a href="#-microcontrollers-modified-into-usb-dongles">ProMicro nRF52840</a> 或 <a href="#-microcontrollers-modified-into-usb-dongles">Seeed Studio XIAO nRF52840</a> 组成，连接 Wi-Fi 天线。

推荐，因为其在制作难度、性能和成本之间取得了良好平衡。

<div class="embeddedVideo">
  <img src="../assets\img\smol-receiver\Lyall_brick_receiver.webp" loading="lazy" class="big-size-image"/>
  来自 <a href="./smol-slimes-community-builds.md#LyallUlric-Stacked-SmolSlime-build">LyallUlric 的堆叠式 SmolSlime 构建</a> 的示例接收器，配备 OOTDTY 2.4G/5.8G 双频天线。
</div>

!!! info
    关于拆除区域和焊接 IPEX 或 SMA 连接器的信息，请参考 <a href="./smol-tracker.md#schematics">Smol 原理图 -> 天线（额外选项）</a>。

##### 社区测试的天线

###### 社区推荐

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>图片</th>
        <th>列表名称</th>
        <th>链接</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <img src="../assets\img\smol-receiver\OOTDTY_2.4G-5.8G_Dual_Band_Antenna_Receiver.webp" loading="lazy" alt="OOTDTY 双频天线" />
        </td>
        <td>
          OOTDTY 5 件 2.4G/5.8G 双频天线 8DBI 高增益内部 PCB 天线，适用于 WiFi 路由器 WiFi 天线
        </td>
        <td>
          <ul>
            <li><a href="https://pl.aliexpress.com/item/4000298368244.html">AliExpress</a></li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>


###### IPX–SMA 转换设置

<div class="table-wrapper">
  <table>
    <thead>
      <tr>
        <th>图片</th>
        <th>列表名称</th>
        <th>备注</th>
        <th>变体</th>
        <th>链接</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>
          <img src="../assets\img\smol-receiver\wifi_antenna.webp" loading="lazy" />
        </td>
        <td>
          2 件迷你橡胶 3dBi 2.4ghz WIFI 天线 SMA 公头路由器蓝牙天线无线模块 2.4g 天线外部天线
        </td>
        <td>测试性能最佳（基于 Lyall 的测试）</td>
        <td>颜色：B</td>
        <td>
          <ul>
            <li><a href="https://www.aliexpress.com/item/1005006686310444.html">AliExpress</a></li>
          </ul>
        </td>
      </tr>
      <tr>
        <td>
          <img src="../assets\img\smol-receiver\wifi_antenna_adapter.webp" loading="lazy" />
        </td>
        <td>
          IPX 转 SMA RF 同轴适配器组件尾纤线缆，SMA 连接器线缆母头转 UFL
        </td>
        <td>
          任何 IPEX 或 SMA 线缆都可以。
          <br />
          在图片标记位置剪断线缆。
        </td>
        <td>优先选择较短线缆。</td>
        <td>
          <ul>
            <li><a href="https://www.aliexpress.com/item/32896039259.html">AliExpress</a></li>
          </ul>
        </td>
      </tr>
    </tbody>
  </table>
</div>

<hr/>

*由 Shine Bright ✨、[Depact](https://github.com/Depact) 和 [Seneral](https://github.com/Seneral) 创建*
