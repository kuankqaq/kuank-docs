# 安装脚本
首先你需要下载一个软件，别担心，[点击即可下载](https://backup.kuank.top/l4script.exe)

下载好之后，先放到一个一万年都不会动的目录，然后双击打开，你会看到一个窗口一闪而过，这是正常的，然后在其他地方下载脚本文件双击运行脚本即可，请务必核查脚本的安全性

如果你的文件被脚本替换了怎么办，没有关系，你会在被替换文件夹的目录下面看到一个叫做`backup-时间戳`的文件夹，将里面的文件拖出来然后全部替换即可，如果你希望删除备份，那也是可以的
### 如何更新
安装软件之后，打开Powershell或者CMD，运行`l4script --update`即可升级，显示无此命令的请重启电脑

这里提供一下脚本的下载网站，[点击即可](https://wwbou.lanzouq.com/i9te83mgt7cf)，解压之后会出现两个文件，都可以双击打开，其中，dxvk那个是安装dxvk的，l4n是安装l4n的

---
### 如何编写脚本
如果你想自己制作一个这样的脚本，你可以直接在txt文件里输入语法并更改后缀名称为`.l4script`即可，下面附上编写脚本的教程

**脚本格式**


以 `---script start---` 作为开始符号
以 `---script end---` 作为结束符号
中间的内容为脚本内容

支持 `#` 开头的注释行

**路径规则**

- 支持 `./` 或 `.\` 表示基于脚本所在目录的相对路径
- 也支持绝对路径
- 支持 `get_game_dir()` 函数自动定位求生之路2游戏目录

**命令列表**

1. mv [source] to [dir] [--files] [--force]
移动文件/目录到指定位置
- 遇到同名文件时自动报错并提示冲突
- 添加 `--force` 参数时先备份冲突文件到 `backup-{时间戳}/` 目录再覆盖
- 添加 `--files` 参数（仅用于目录）只移动目录内的文件，不移动目录本身

2. cut [source] to [dir] [--files] [--force]
同 mv，剪切文件/目录到指定位置

3. cp [source] to [dir] [--force]
复制文件/目录到指定位置
- 遇到同名文件时自动报错并提示冲突
- 添加 `--force` 参数时先备份冲突文件到 `backup-{时间戳}/` 目录再覆盖

4. mkdir [dir]
创建目录（支持多级嵌套目录）

5. down [url] [to [dir]] [as filename]
下载文件
- 不填 `to` 默认下载到脚本所在目录
- 使用 `as` 可以自定义文件名（包括扩展名）
- 支持逗号分隔多个URL批量下载
- 显示下载进度条

6. unzip [file] [to [dir]] [---del-source] [--force]
解压文件
- 支持 `.zip`、`.rar`、`.7z`、`.tar.gz`、`.tgz` 格式
- 不填 `to` 默认解压到压缩包所在目录
- 原子性解压：先解压到临时目录，全部成功后再合并到目标目录
- 遇到同名文件时自动报错并提示冲突
- 添加 `--force` 参数时先备份冲突文件到 `backup-{时间戳}/` 目录再覆盖
- 添加 `---del-source` 参数可在解压完成后删除源压缩包
- 显示解压进度条

7. print "message"
在命令行显示文本
- 使用双引号或单引号包裹消息内容
- 脚本中包含 print 时，执行完毕后会等待用户按回车键退出

8. mkdir [dir]
创建目录（支持多级嵌套目录）

**命令行参数**

l4script (无参数)
显示用法提示

l4script check <script.l4script>
检查脚本语法，不实际执行
- 语法正确输出 `语法检查通过！`
- 语法错误输出具体错误信息

**内置函数**

get_game_dir([subdir])
自动寻找电脑上求生之路2 (Left 4 Dead 2) 的安装目录
- `get_game_dir()` — 返回游戏根目录，如 `D:\steam\steamapps\common\Left 4 Dead 2`
- `get_game_dir(vpk)` — 返回 `left4dead2\addons` 路径
- `get_game_dir(./left4dead2/bin)` — 支持相对路径，返回 `游戏安装目录/left4dead2/bin`
- 通过Steam注册表自动定位，支持多库文件夹

检查更新
- **手动检查**: 运行 `l4script --update` 检查并下载更新
- **自动检查**: 每次运行脚本时后台静默检查，有新版本会在控制台提示

更新流程
1. 检查远程版本信息
2. 对比当前版本，有新版本提示用户确认
3. 下载新版到临时目录
4. 生成批处理脚本替换当前程序
5. 自动重启新版程序

## 脚本示例

```
---script start---

# 显示欢迎信息
print "开始执行任务..."

# 创建目录
mkdir ./temp/extracted

# 移动文件
mv ./data/file.txt to ./backup/

# 只移动目录内的文件（不移动目录本身）
mv ./mods to get_game_dir(vpk) --files

# 复制文件到游戏目录
cp ./xxx.vpk to get_game_dir(vpk)

# 下载文件（默认到脚本目录）
down https://example.com/file.zip

# 下载并重命名
down https://example.com/file.zip as mymod.vpk

# 解压并删除源文件
unzip ./downloads/file.zip to ./extracted/ ---del-source

# 强制解压（冲突文件自动备份到 backup-{时间戳}/）
unzip ./update.zip to get_game_dir(vpk) --force

print "任务完成！"

---script end---
```

**备份功能**

使用 `--force` 参数覆盖文件时，被替换的文件会备份到 `backup-{Unix时间戳}/` 目录，例如：
```
backup-1743840000/
backup-1743840060/
```
每次覆盖生成独立的时间戳文件夹，不会互相覆盖。