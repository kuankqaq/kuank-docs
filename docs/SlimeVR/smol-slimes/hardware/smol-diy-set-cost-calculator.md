# Smol DIY 套装成本计算器

!!! info
    默认选中的值旨在提供最佳性价比。
    
    要获得更好的性能，请将选择更改为以下值：
    - IMU：ICM-45686


## 选择追踪器数量

开始之前，请先确定[您可能需要多少个追踪器](../../user-guide/slimevr101.md#how-many-trackers-do-you-need)。

<div class="radio-card-group">
  <div class="radio-card">
    <input type="radio" name="diy-set" value="5" id="trackers-5" />
    <label for="trackers-5">
      <div class="radio-card-name">下半身套装</div>
      <div class="radio-card-desc">5 个 IMU &mdash; 休闲 VR 用户</div>
      <div class="radio-card-desc">
        提供腿部和脊柱的位置追踪。脚部方向和下脊柱弯曲的追踪有限。
      </div>
    </label>
  </div>
  <div class="radio-card">
    <input type="radio" name="diy-set" value="6" id="trackers-6" checked="checked" />
    <label for="trackers-6">
      <div class="radio-card-name">核心套装</div>
      <div class="radio-card-desc">6 个 IMU &mdash; 想要更好稳定性的用户</div>
      <div class="radio-card-desc">
        增加一个额外的脊柱追踪器以改善稳定性，尤其是在坐下、躺下或弯腰时。
      </div>
    </label>
  </div>
  <div class="radio-card">
    <input type="radio" name="diy-set" value="8" id="trackers-8" />
    <label for="trackers-8">
      <div class="radio-card-name">增强核心套装</div>
      <div class="radio-card-desc">8 个 IMU &mdash; 经常坐下或躺下的用户</div>
      <div class="radio-card-desc">
        增加脚步追踪，以便在坐着或躺着时做出更具表现力和情感化的姿势。
      </div>
    </label>
  </div>
  <div class="radio-card">
    <input type="radio" name="diy-set" value="10" id="trackers-10" />
    <label for="trackers-10">
      <div class="radio-card-name">全身套装</div>
      <div class="radio-card-desc">10 个 IMU &mdash; 舞者、角色扮演者、沉浸式用户</div>
      <div class="radio-card-desc">
        实现独立的肘部运动，提供更逼真的上半身动作并增强 VR 沉浸感。
      </div>
    </label>
  </div>
  <div class="radio-card">
    <input type="radio" name="diy-set" value="16" id="trackers-16" />
    <label for="trackers-16">
      <div class="radio-card-name">豪华追踪器套装</div>
      <div class="radio-card-desc">16 个 IMU &mdash; 动作捕捉专业人士、动画师</div>
      <div class="radio-card-desc">
        可用于不带 VR 设备的动作捕捉，分成两套增强核心套装，或根据需要进行定制，以实现灵活性和精确度。
      </div>
    </label>
  </div>
</div>

## 选择部件

<div class="table-wrapper">
    <table>
        <thead>
            <tr>
                <th>组件</th>
                <th style="width:70%">选择</th>
                <th>数量</th>
                <th>单价</th>
                <th>含运费价格</th>
                <th style="min-width: 200px">快速链接</th>
            </tr>
        </thead>
        <tbody id="diy-components">
        </tbody>
    </table>
</div>

<div class="total-cost">
  <strong>总价：</strong>
  ~<span id="diy-total-value"></span>
</div>

## 详细说明

- 一个接收器支持 10 个追踪器，但建议每个接收器最多 8 个追踪器。
- 401230 3.7V 110 mAh 电池通常可提供 40-60 小时的电池续航，具体取决于使用情况和组件。

## 获取部件后的步骤

收集好部件后，构建完整功能套装还需以下步骤：
1. [Smol 追踪器焊接](./smol-tracker-soldering.md)
2. [Smol 刷写固件](../firmware/smol-flashing-firmware.md)
3. [Smol 配对与校准](../firmware/smol-pairing-and-calibration.md)

<hr/>

*由 Shine Bright ✨ 和 [Depact](https://github.com/Depact) 创建*

<script type="module" src="../assets/js/smol-building-calculator/index.js"></script>

<style>
table thead th,
table tbody td {
    padding: 3px 10px;
}

fieldset {
    border-radius: 8px;
}

.total-cost {
    padding-top: 10px;
    font-size: large;
}

.radio-card-group {
    padding-top: 10px;
    padding-bottom: 10px;
    display: flex;
    flex-direction: column;
    margin-bottom: 10px;
}

@media (min-width: 50rem) {
    .main {
        max-width: 1100px !important;
    }
}

select {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border-radius: 5px;
}

td:first-of-type {
    border-left: 1px solid #eeebee;
}

:root {
  --content-max-width: 2000px;
}

td label {
  padding-bottom: 10px;
}

.radio-card-group {
    padding-top: 10px;
    padding-bottom: 10px;
}

.radio-card {
    border: 1px solid var(--theme-popup-border);
    border-radius: 6px;
    padding: 8px;
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 12px;
}

/* Outline for selected card */
.radio-card:has(input[type="radio"]:checked) {
    outline: 2px solid var(--sidebar-active);
    outline-offset: 2px;
}

.radio-card-info {
    flex: 1;
}

.radio-card-name {
    font-weight: bold;
}

.radio-card-desc {
    font-size: 0.95em;
}

.radio-card-cost {
    font-weight: bold;
    margin-left: 16px;
}
</style>
