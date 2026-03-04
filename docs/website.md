# 模组站须知

### 1.上传模组

地图站支持markdown格式文本，故如果会的话可以书写markdown格式简介，一般来说，地图标题格式使用如下格式

> 中文名 (英语名称)

填写信息一般建议地图类填写来源链接(工坊或gamemap)、下载链接(小于100mb用蓝奏云，大于用123云盘)、简介

地图代码(代码获取方法，下载[vpkedit](https://wwbou.lanzouq.com/iswdA3jsoaxi)密码hd03，安装之后打开vpk文件，多part文件则打开part1，打开文件之后进入missions文件夹里面的唯一一个txt，往下面翻，翻到被coop包裹的代码，如下

```json
"coop"
		{
			"1"
			{
				"Map" "C29_LastResort_1" #示例地图代码
				"DisplayName" "Last Resort 1"
				"Image" "lastresort\l4d_lastresort1"
			}

			"2"
			{
				"Map" "C29_LastResort_2"
				"DisplayName" "Last Resort 2"
				"Image" "lastresort\l4d_lastresort2"
			}

			"3"
			{
				"Map" "C29_LastResort_3"
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



即可，需全部复制map中包裹的名称，如 zc_m1 ，注意不是displayname）

标签可选可不选

### 2.关于网站

网站另配有API，基础地址为 https://api.kuank.top

开发者为宽宽