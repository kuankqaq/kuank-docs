# 模组站须知

### 1.上传模组

地图站支持markdown格式文本，故如果会的话可以书写markdown格式简介，一般来说，地图标题格式使用如下格式

> 中文名 (英语名称)

填写信息一般建议地图类填写来源链接(工坊优先，gamemap其次)、下载链接(小于100mb用蓝奏云zip，大于用123云盘7z压缩包)、简介、地图代码

代码获取方法，下载 [Vpkedit](https://wwbou.lanzouq.com/iswdA3jsoaxi) 密码hd03
安装之后打开vpk文件，多part文件则打开part1，打开文件之后进入missions文件夹里面的唯一一个txt，往下面翻，翻到被coop包裹的代码，如下例

```json
"coop" #代表战役地图
		{
			"1"
			{
				"Map" "C29_LastResort_1" #示例地图代码
				"DisplayName" "Last Resort 1"
				"Image" "lastresort\l4d_lastresort1"
			}

			"2"
			{
				"Map" "C29_LastResort_2" #这个是m2
				"DisplayName" "Last Resort 2"
				"Image" "lastresort\l4d_lastresort2"
			}

			"3"
			{
				"Map" "C29_LastResort_3" #以此类推
				"DisplayName" "Last Resort 3"
				"Image" "lastresort\l4d_lastresort3"
			}

			"4"
			{
				"Map" "C29_LastResort_4"
				"DisplayName" "Last Resort 4"
				"Image" "lastresort\l4d_lastresort4"
			}
		}
	
```



即可，需全部复制map中包裹的名称，如 zc_m1 ，注意不是 `displayname`）

标签可选可不选

### 2.网站审核
在提交好你的第一个模组之后，你肯定会想到何时审核的问题，对此对审核的时效性以及常见问题进行一个解释

- 1. 一般模组在审核后24小时内将返回结果，最迟不晚于48小时之内
- 2. 拒绝的模组将在14天后自动删除
- 3. 请不要在群中**催促**与**骚扰**地图站或群管理请求审核，这非常不礼貌，而且你不是来群里当大爷的 ~~，除非你打的钱很多~~
- 4. 请在提交之前**务必**在地图站中寻找是否有相同的地图，如果你想更新地图，请联系地图站管理


### 3.关于网站

网站另配有API，基础地址为 https://api.kuank.top
欲想获取详细文档，还请私信开发者
开发者为宽宽