# Smol 串行和按钮命令

#### 接收器命令

* info - 获取接收器信息
* list - 获取已配对的追踪器
* eboot - 软复位接收器
* pair - 进入配对模式
* dd <address> - 手动添加追踪器
* emove - 移除最后配对的追踪器
* exit - 退出配对模式
* clear - 清除已存储的追踪器
* dfu - 进入 DFU 引导加载程序
* uptime - 获取接收器运行时间
* meow - 喵！

#### 追踪器命令

* info - 获取追踪器信息
* eboot - 软复位追踪器
* attery - 获取电池信息
* scan - 重新扫描传感器
* calibrate - 校准传感器 ZRO
* 6-side - 校准 6 面加速度计
* mag - 清除磁力计校准
* pair - 进入配对模式
* set <address> - 手动设置接收器（必须先完成接收器的 `dd` 命令）
* clear - 清除配对数据
* dfu - 进入 DFU 引导加载程序
* uptime - 获取追踪器运行时间
* debug - 打印调试日志以排查追踪器或固件问题
* eset <type> - 重置 "zro"、"acc"（仅限 6 面已启用）、"mag"、"bat" 或 "all" 的校准/统计
* meow - 喵！

#### 按钮快捷键

* 复位 - 按 1 次
* 校准 - 按 2 次
* 配对模式 - 按住 5 秒
* DFU 引导加载程序 - 按 4 次
* 深度睡眠 - 按住 1 秒

---

*由 Shine Bright ✨、[Depact](https://github.com/Depact) 和 [Seneral](https://github.com/Seneral) 创建。由 [Brisfknibis](https://github.com/brisfknibis) 编辑。*
